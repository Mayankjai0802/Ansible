FROM centos:8

RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-* \
 && sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-* \
 && dnf update -y \
 && dnf install httpd -y \
 && dnf clean all

COPY index.html /var/www/html/index.html
COPY run.sh ./run.sh
RUN chown apache:apache /var/www/html/index.html && chmod +x ./run.sh

CMD ["./run.sh"]