FROM centos:latest

# Edit sudoers file
# To avoid error: sudo: sorry, you must have a tty to run sudo
RUN touch /etc/sudoers
RUN sed -i -e "s/Defaults    requiretty.*/ #Defaults    requiretty/g" /etc/sudoers

# Install the NodeJS 6
RUN curl --silent --location https://rpm.nodesource.com/setup_8.x | bash -&&\
    yum -y install nodejs

# Install ssh server

RUN yum -y update; yum clean all
RUN yum -y install openssh-server passwd; yum clean all
RUN mkdir /var/run/sshd

RUN ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N ''

RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config
RUN sed -ri 's/#UsePAM no/UsePAM no/g' /etc/ssh/sshd_config

##############################################

WORKDIR app
ADD package.json /app
ADD package-lock.json /app
ADD src /app/src
ADD public /app/public

RUN npm i

CMD ["npm", "start"]

#ENTRYPOINT ["/usr/sbin/sshd", "-D"]
