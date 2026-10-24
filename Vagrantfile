PROVIDER = ENV["VAGRANT_DEFAULT_PROVIDER"] || "virtualbox"
BOX_NAME = ENV['VAGRANT_BOX'] || 'bento/ubuntu-22.04'

Vagrant.configure("2") do |config|
  config.vm.box = BOX_NAME

  # Общие настройки ресурсов
  config.vm.provider :virtualbox do |v|
    v.memory = 1512
    v.cpus = 2
  end

  config.vm.provider :libvirt do |lv|
    lv.memory = 1512
    lv.cpus = 2
  end

  boxes = [
    { name: "backup", ip: "192.168.56.160" },
    { name: "client", ip: "192.168.56.150" }
  ]

  boxes.each do |opts|
    config.vm.define opts[:name] do |vm|
      vm.vm.hostname = opts[:name]
      vm.vm.network "private_network", ip: opts[:ip]

      # Диск только для backup
      if opts[:name] == "backup"
        # VirtualBox: создать и подключить .vdi
        vm.vm.provider :virtualbox do |vb|
          disk_path = "./backup_disk.vdi"
          size_mb = 5120  # 5 ГБ

          unless File.exist?(disk_path)
            vb.customize ["createhd", "--filename", disk_path, "--size", size_mb.to_s]
          end

          vb.customize [
            "storageattach", :id,
            "--storagectl", "SATA Controller",
            "--port", 1,
            "--type", "hdd",
            "--medium", disk_path
          ]
        end

        # Libvirt: подключить существующий или создать .qcow2 (через qemu-img на хосте)
        vm.vm.provider :libvirt do |lv|
          # Для libvirt Vagrant не умеет сам создавать диск — его нужно создать заранее на хосте:
          #   qemu-img create -f qcow2 backup_disk.qcow2 5G
          disk_path = "./backup_disk.qcow2"

          lv.disk :file => disk_path,
                  :device => "disk",
                  :bus => "sata",
                  :cache => "none"
        end
      end
    end
  end
end
