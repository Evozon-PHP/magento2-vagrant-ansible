# Simple Vagrant project for Magento 2 with Ansible.

 * [What You get](#what-you-get)
 * [How to install](#how-to-install)
   * [Requirements](#requirements)
   * [Installation steps](#installation-steps)
 * [Default credentials and settings](#default-credentials-and-settings)
   * [Web access](#web-access)
   * [Codebase and DB access](#codebase-and-db-access)

## What You get

It is expected that Magento 2 project source code will be located and managed on the host.

Development Environment:

 1. [Ubuntu vagrant box](https://atlas.hashicorp.com/ubuntu/boxes/trusty64)
 2. Developer tools:
 	- git
 	- vim
 	- curl
 	- htop
 	- wget
 	- composer
 3. NGINX
 4. PHP 7.0.x with all extensions necessary for Magento 2: cli, intl, mcrypt, culr, pear, fpm, mbstring, mysql, xls, imagick, gd, opcache, zip
 5. MySQL 5.6
 6. XDebug
 7. Installs Magento 2

## How to install

Please read [Vagrant Docs](https://docs.vagrantup.com/v2) if you never used Vagrant before.

### Requirements

Software listed below should be available in [PATH](https://en.wikipedia.org/wiki/PATH_\(variable\)) (except for PHP Storm).

- [Vagrant 1.8+](https://www.vagrantup.com/downloads.html)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- [Ansible](http://docs.ansible.com/ansible/)
- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

### Installation steps

 1. Open terminal and navigate into the directory to the one which you want to contain Magento project.

 1. Clone (download) project with Vagrant configuration:

   ```bash
   git clone git@github.com:Evozon-PHP/magento2-vagrant-ansible.git magento2
   ```

 1. Change directory, navigate to project directory:

	```bash
    cd ./magento2
	```
 1. Config Environment:

	```bash
    vim ansible/vars/variables.yml
	```
    
    ```yaml
    magento:
	    install: '0'
    	install_sample: '1'
	    db_name: magento
    	db_password: magento
	    db_user: magento
    	admin_user: admin
	    admin_password: admin123admin
	    admin_firstname: John
    	admin_lastname: Doe
	    admin_email: john.doe@example.com
	    public_key: MAGENTO_PUBLIC_KEY_HERE
    	private_key: MAGENto_PRIVATE_KEY_HERE
	```

 1. Start up virtual machine and Install Magento2:

	```bash
    vagrant up
	```

 1. Point a host name to VM Private Network IP in /etc/hosts:

	```bash
    sudo echo '192.168.33.99 magento2.local' >> /etc/hosts
	```

## Default credentials and settings

Some of default settings are available for override.
Upon a successful installation, you'll see the location and URL of the newly-installed Magento 2 application in console.

### Web access
- Access storefront at `http://magento2.local`
- Access admin panel at `http://magento2.local/admin/`
- Magento admin user/password: `admin/admin123admin`

### Codebase and DB access
- MySQL DB host: `localhost` (not accessible remotely)
- MySQL DB name: `magento`
- MySQL DB user/password: `magento:magento`.
