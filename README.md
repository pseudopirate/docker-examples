# docker-examples

### local
`sudo docker build -t local .`

`sudo docker run --rm -p 3000:3000 -v /your/absolute/path/to/project/src:/app/src local`


## remote
`sudo docker build -t remote .`

`sudo docker run -d -p 3000:3000 -p 8000:22 --name remote remote`

`sudo docker exec -it remote bash`

Inside the container:
- add password:
`passwd`

- run ssh server
`/usr/sbin/sshd`

- exit from container

Now you are able to connect to your container via ssh protocol on 8000 port.

Watch application logs:
`sudo docker logs -f remote`
