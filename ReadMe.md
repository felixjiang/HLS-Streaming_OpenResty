
Build an image from Dockerfile
``docker build -t <image-name> <dockerfile-path>`

Run a container in the background (detached) from an image with port and volume mappings
`docker run --name <container-name> <image`
`sudo docker run -d --name openresty_encrypted --network streaming_network -p 8080:80 -p 8443:443 -p 1935:1935 -v /etc/cjiang/hls_encrypted:/tmp/hls openresty-rtmp-hls-encrypted`

Run a container in interactive mode
`sudo docker run -it --name ffmpeg-test --network streaming_network ffmpeg-rpi`

Push video stream
`ffmpeg -re -i file_example_MP4_1280_10MG.mp4 -c copy -f flv -flvflags no_duration_filesize rtmp://openresty_encrypted/hls/stream_name`

Switch to a container command-line in the docker environment
`docker exec -it openresty_encrypted bash`
ls /tmp/hls/

List running | all containers
`docker ps` | `docker ps -a`


cp /tmp/hls/keys/stream_name-0.key /usr/local/openresty/nginx/html/stream_name-0.key
https://ddns-kangcheng.microfish.win:8443/hls/stream_name.m3u8


## Git commands

git checkout <branch-name>

git checkout -b <branch_name>: create a branch and switch to it

git add . | git add <file-name>

git commit -m '<comment>'

git push origin | git push origin <branch-name>


git init

git remote add <remote-git-URL>

git remote set-url origin <new-remote-git-URL>

git remote -v

git branch: show the branch you are currently on

git push -u origin <branch-name>: Push the branch-name to origin with upstream tracking

git status: list changes you made in the branch you are currently on 


git clone <git-repo-URL>: clone a remote git repo to local with the origin being the remote repo

git pull origin | git pull origin <branch-name>: get the commits on origin and merge them to the branch you are currently on
