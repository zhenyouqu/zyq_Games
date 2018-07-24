1.创建存放Dockerfile的目录
#例如mkdir ubuntu_game
2.cd到那个目录里面
#例如cd ubuntu_game
3.如果需要从宿主机上面拷贝文件到镜像里面,需要把文件先拷贝到ubuntu_game目录下面
4.docker build -t ubuntu_game_0724 .
#ubuntu_game_0724是镜像的名字，这个名字可以自定义

