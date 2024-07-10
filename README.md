Docker Containerization for Django

Docker installation on the server:
sudo apt update
sudo apt install docker.io -y
sudo systemctl status docker
sudo systemctl start docker

![image](https://github.com/surumivs/Docker/assets/170710844/1cff2ab4-d098-40f8-b6f3-08d35c0306bc)

 
Grant Access to your user to run docker commands
sudo usermod -aG docker ubuntu
docker run hello-world (verify)
Clone this repository and move to example folder
git clone https://github.com/surumivs/Docker.git

 ![image](https://github.com/surumivs/Docker/assets/170710844/e7a9a36f-f93e-490f-8807-5a5c55cf900f)

cd /Docker-Zero-to-Hero/examples/python-web-app/devops/
1.	Install Django-admin will create skeleton files and folders
django-admin startproject devops(creating db.sqlite3, devops, manage.py)
2.	Install application with the below command
Python manage.py startapp demo(created demo folder)
cd demo
mkdir templates
vi demo_site.html(Create app page)
3.	Create Dockerfile on /Docker-Zero-to-Hero/examples/python-web-app/
FROM ubuntu

WORKDIR /app

COPY requirements.txt /app
COPY devops /app

RUN apt-get update && \
    apt-get install -y python3 python3-venv && \
    python3 -m venv /app/venv && \
    /app/venv/bin/pip install --upgrade pip && \
    /app/venv/bin/pip install -r requirements.txt

ENV PATH="/app/venv/bin:$PATH"

ENTRYPOINT ["python3"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]

4.	Create requirements.txt there
Django
Tzdata

![image](https://github.com/surumivs/Docker/assets/170710844/8755905c-8162-47f6-ab03-de056b757c16)

 
Login to Docker [Create an account with https://hub.docker.com/]
docker login
docker build .
docker images
docker run -p 8000:8000 -it <image-id>


Now, call on your favorite browser Error! Hyperlink reference not valid.
DONE!!!!!!!!!!!
 
![image](https://github.com/surumivs/Docker/assets/170710844/5d9767ba-373c-4d05-a108-b31a5435f3a6)

