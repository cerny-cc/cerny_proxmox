# cerny_proxmox

TODO: Enter the cookbook description here.

function bp {
    rm cookbooks*.tar.gz
    berks update
    berks package
    git add cookbooks*.tar.gz
}

bp
git add .
git commit -sm "commit message"
git push
chef-client -z -r 'cerny_proxmox::default' --recipe-url=https://github.com/cerny-cc/cerny_proxmox/raw/master/cookbooks-1481410031.tar.gz


/usr/local/bin/proxmox-deploy --proxmox-host pve01.infra.cerny.cc --cloud-images-dir /mnt/pve/gluster/templates/cloud
