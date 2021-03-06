# -*- mode: ruby -*-
# vi: set ft=ruby :

# Developer: Eddy Lackmann
# Github:https://github.com/eddylackmann 
# Last update: 24 June 2020
# Email: a.eddy@hotmail.de

# Vagrant Configuration for Limesurvey
Vagrant.configure("2") do |config|
 
  #LimeSurvey Master Machine
  config.vm.define "master" do |master|
      # Latest version of Ubuntu. Feel free to update it.
      master.vm.box = "ubuntu/focal64"

      #Custom variable for installation
      ip                = "10.0.0.10"
      #php setup
      phpversion        = "7.4" 
      #mysql setup
      mysqlRootPass     = "password"
      mysqlDBName       = "limesurvey"
      mySqlDBUser       = "limesurvey"
      mySqlDBPassword   = "password"
      #postgres setup
      postgresDB        = "limesurvey"
      postgresPassword  = "password"
      #limesurvey setup
      limeSurveyBranch  = "master"
      #IDE KEY for Xdebug
      ideKey  = "VSCODE"
     
      #shared webfolder
      master.vm.synced_folder "./master", "/var/www", :mount_options => ["dmode=777", "fmode=666"], create:true
      #copy configuration
      master.vm.provision "file", source: "./configuration", destination: "/var/www/configuration"
      #provision file 
      master.vm.provision "shell", path: "provision/provision.sh", :args => [ip, phpversion,mysqlRootPass,mysqlDBName,mySqlDBUser,mySqlDBPassword,postgresDB,postgresPassword,limeSurveyBranch,ideKey]
      #machine ip
      master.vm.network "private_network", ip: ip
      #machine hostname
      master.vm.hostname = "LimeSurveyMaster"
      
      # Needed for Windows 10 host, so ubuntu package are reachable and we can install the VirtualBox Guest Additions
      master.vm.provider "virtualbox" do |vb|
        vb.name = "LimeSurveyMaster"
        vb.memory = 1024
        vb.cpus = 2
        #enable this line on windows machine (Optional).
        #vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      #create serial port / Needed for ubuntu 20.04
      vb.customize [ "modifyvm", :id, "--uartmode1", "file", File::NULL ]
      end
  end

  #LimeSurvey Develop Machine
  config.vm.define "develop" do |develop|
    # Latest version of Ubuntu. Feel free to update it.
    develop.vm.box = "ubuntu/focal64"
    
    #Custom variable for installation
    ip                = "10.0.0.20"
    #php setup
    phpversion        = "7.4" 
    #mysql setup
    mysqlRootPass     = "password"
    mysqlDBName       = "limesurvey"
    mySqlDBUser       = "limesurvey"
    mySqlDBPassword   = "password"
    #postgres setup
    postgresDB        = "limesurvey"
    postgresPassword  = "password"
    #limesurvey setup
    limeSurveyBranch  = "develop"
    #IDE KEY for Xdebug
    ideKey  = "VSCODE"

    #shared webfolder
    develop.vm.synced_folder "./develop", "/var/www", :mount_options => ["dmode=777", "fmode=666"], create:true
    #copyconfiguration
    develop.vm.provision "file", source: "./configuration", destination: "/var/www/configuration"
    #provision file 
    develop.vm.provision "shell", path: "provision/provision.sh", :args => [ip, phpversion,mysqlRootPass,mysqlDBName,mySqlDBUser,mySqlDBPassword,postgresDB,postgresPassword,limeSurveyBranch,ideKey]
    #machine ip
    develop.vm.network "private_network", ip: ip
    #machine hostname
    develop.vm.hostname = "LimeSurveyDevelop"
    
    # Needed for Windows 10 host, so ubuntu package are reachable and we can install the VirtualBox Guest Additions
    develop.vm.provider "virtualbox" do |vb|
      vb.name = "LimeSurveyDevelop"
      vb.memory = 1024
      vb.cpus = 2
      #enable this line on windows machine (Optional).
      #vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      #create serial port / Needed for ubuntu 20.04
      vb.customize [ "modifyvm", :id, "--uartmode1", "file", File::NULL ]
    end
  end

  #LimeSurvey LTS Machine
  config.vm.define "lts" do |lts|
    #Latest version of Ubuntu. Feel free to update it.
    lts.vm.box = "ubuntu/focal64"
    
    #Custom variable for installation
    ip                = "10.0.0.30"
    #php setup
    phpversion        = "7.4" 
    #mysql setup
    mysqlRootPass     = "password"
    mysqlDBName       = "limesurvey"
    mySqlDBUser       = "limesurvey"
    mySqlDBPassword   = "password"
    #postgres setup
    postgresDB        = "limesurvey"
    postgresPassword  = "password"
    #limesurvey setup
    limeSurveyBranch  = "3.x-LTS"
    #IDE KEY for Xdebug
    ideKey  = "VSCODE"

    #shared webfolder
    lts.vm.synced_folder "./lts", "/var/www", :mount_options => ["dmode=777", "fmode=666"], create:true
    #copyconfiguration
    lts.vm.provision "file", source: "./configuration", destination: "/var/www/configuration"
    #provision file 
    lts.vm.provision "shell", path: "provision/provision.sh", :args => [ip, phpversion,mysqlRootPass,mysqlDBName,mySqlDBUser,mySqlDBPassword,postgresDB,postgresPassword,limeSurveyBranch,ideKey]
    #machine ip
    lts.vm.network "private_network", ip: ip
    #machine hostname
    lts.vm.hostname = "LimeSurveyLTS"
    # Needed for Windows 10 host, so ubuntu package are reachable and we can install the VirtualBox Guest Additions
    lts.vm.provider "virtualbox" do |vb|
      vb.name = "LimeSurveyLTS"
      vb.memory = 1024
      vb.cpus = 2
      #enable this line on windows machine (Optional).
      #vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      #create serial port / Needed for ubuntu 20.04
      vb.customize [ "modifyvm", :id, "--uartmode1", "file", File::NULL ]
    end
  end

end
