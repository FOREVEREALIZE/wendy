FROM ubuntu:focal

# Add Oracle Public Keys
RUN wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | apt-key add -
RUN wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | apt-key add -

# Add VirtualBox Repository
RUN echo "deb [arch=amd64] http://virtualbox.org/virtualbox/debian $(lsb_release -cs) contrib" | tee /etc/apt/sources.list.d/virtualbox.list
RUN apt update -y

# Install Virtualbox 6.1.x
RUN apt install virtualbox-6.1

# Add Vagrant Public Key
RUN wget -q https://apt.releases.hashicorp.com/gpg -O- | sudo apt-key add -

# Add Vagrant Repository
RUN echo "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | tee /etc/apt/sources.list.d/vagrant.list
RUN apt update -y

# Install Vagrant
RUN apt install vagrant
