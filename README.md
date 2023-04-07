# python-shell-docker
launch a python shell in docker and pass .py file as argument to the container and get the output


---
create python file `nano test.py`

write the code

save and exit `ctrl+s` `ctrl+x`

---

create Dockerfile `nano Dockerfile`

```
FROM centos
RUN cd /etc/yum.repos.d/
RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
RUN sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
RUN yum install python39 -y

ENTRYPOINT ["python3"]
CMD ["-c test.py"]
```

build image `sudo docker build -t python-shell .`

launch container `sudo docker run --rm -it python-shell "-c$(cat test.py)"`

![image](https://user-images.githubusercontent.com/46744784/230546971-70846122-6ee1-4048-a35e-6d3084ebe5ce.png)

![image](https://user-images.githubusercontent.com/46744784/230547065-da2c33fc-c5de-48b9-97be-bf2460da8d12.png)
