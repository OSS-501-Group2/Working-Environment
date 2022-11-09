Working Environment
===
***
## What for?
Open Source Final 프로젝트는 기본적으로 Linux기반의 환경에서 테스팅 및 실습이 이루어져야 합니다. 팀원들의 PC가 주로 Windows 환경이고,VMWare 자체가 많이 무겁다 보니, 제 서버에 RHEL Cent OS 8기반 개인 SSH 환경을 띄워 팀원들이 작업할 수 있도록 진행하였습니다. 
***
## Image information
- Base : Cent OS:latest
- Volume
    - /home
- Port
    - 22 : For ssh
- Privileged : True (Require system D-Bus)
- SSH base account 
    - user : root
    - pw : centos123
***
## How in use?
1. Build container image

```bash
docker build -t (image name) .
```

2. Run container and execute essential shell script : You don't need additional python installation of using `init.py` script

```
# With docker command
docker run -d --privileged --name (container name) -v $(pwd)/(local mount directory):/home -p 9101:22 --restart=unless-stopped (image name) /sbin/init 
&& 
docker exec (container name) entrypoint.sh

# With init script
# -n : name of docker container
# -v : local volume mount ex) sure things but $(pwd)...etc is available also
# -p : port
# -i : image name
python3 init.py -n (value) -v (value) -p (value) -i (value)
```
***
## Example Feature
<img width="932" alt="image" src="https://user-images.githubusercontent.com/45956041/200820255-333c7e8c-6ac5-4e8d-a16d-8f20802ffb07.png">
