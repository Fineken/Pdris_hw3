FROM willhallonline/ansible

# Установка пакетов и настройка SSH
RUN apk --update add --no-cache openssh \
    && sed -i 's/#PermitRootLogin.*/PermitRootLogin yes/' /etc/ssh/sshd_config \
    && echo "root:1234" | chpasswd \
    && rm -rf /var/cache/apk/* \
    && sed -i 's/#Port 22/Port 22/g' /etc/ssh/sshd_config \
    && /usr/bin/ssh-keygen -A \
    && ssh-keygen -t rsa -b 4096 -f /etc/ssh/ssh_host_key \
    && echo "export VISIBLE=now" >> /etc/profile \
    && echo "AllowAgentForwarding yes" >> /etc/ssh/sshd_config \
    && echo "PermitRootLogin yes" >> /etc/ssh/sshd_config \
    && echo "X11UseLocalhost no" >> /etc/ssh/sshd_config \
    && echo "X11Forwarding yes" >> /etc/ssh/sshd_config
RUN apk --no-cache add docker docker-compose
# Установка утилиты ping
RUN apk add --no-cache iputils

# Откройте порт 22 для SSH и ICMP (пинг)
EXPOSE 22

WORKDIR DeployerData
ADD . .

# Запуск SSH-сервера и Ansible
CMD ["/usr/sbin/sshd", "-D"]
