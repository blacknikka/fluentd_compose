
FROM centos

# タイムゾーン変更
RUN cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

# yum アップデートとcronのインストール
RUN yum update -y --disableplugin=fastestmirror && \
    yum install -y epel-release --disableplugin=fastestmirror && \
    yum install -y --disableplugin=fastestmirror sudo cronie

RUN groupadd -g 1000 developer && \
    useradd  -g      developer -m -s /bin/bash dev-user && \
    echo 'dev-user    ALL=(ALL)    NOPASSWD:ALL' >> /etc/sudoers.d/dev-user

# PAMの設定
RUN sed -i -e '/pam_loginuid.so/s/^/#/' /etc/pam.d/crond

# scriptの保存
ADD cron.d /etc/cron.d/
RUN chmod 0644 /etc/cron.d/*

CMD crond && tail -f /dev/null