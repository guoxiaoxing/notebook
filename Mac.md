## Mac常用命令

```
# 删除所有.DS_Store文件
sudo find / -name '.DS_Store' -print -delete
# 删除当前目录下所有空子目录 
find . -type d -empty -delete -print

# 找出目录下大于100M的文件
find . -type f -size +100000k 
find . -type f -size +100000k -exec ls -lh {} \; | awk '{ print $5 " => " $9 " " $10 }' 

# 使用tail实时监控日志
tail -fn 500 /var/log/messages #参数-f使tail不停地去读最新的内容，这样有实时监视的效果

# 分割和合并文件
split -b 300m BIGFILE PREFIX
cat PREFIX* > BIGFILE

# 查看目录大小
du -sh /opt
# 查看本地磁盘使用信息
df -h

# 查看当前使用的SHELL名称
echo $SHELL
echo $0
env | grep SHELL
cat /etc/passwd | grep USERNAME

# SCP常用操作
# 获取远程服务器上的文件
scp -P 22 admin@192.168.1.96:/home/admin/test.tar.gz ~/test.tar.gz
# 获取远程服务器上的目录
scp -P 22 -r admin@192.168.1.96:/home/admin/test/ ~/test
# 将本地文件上传到服务器上
scp -P 22 /home/james/test.tar.gz admin@192.168.1.96:/home/admin/test.tar.gz
# 将本地目录上传到服务器上
scp -P 22 -r /home/james/test/ admin@192.168.1.96:/home/admin/test


# 批量重命名文件
# 本例演示了把当前目录下的所有MP3文件的名称去除多余的字符，只保留序号。
rename 's/.+(\d+).mp3/$1.mp3/' *.mp3

# 批量下载整个网站
wget -r -np http://www.sandpile.org/

# 批量Unlock文件
chflags -R nouchg /PATH/TO/DIRECTORY/WITH/LOCKED/FILES/

# 一些查看用户和系统信息的命令
id
finger
uname -a
ulimit -a
···


## Finder显示默认隐藏的文件

```
# 显示所有隐藏文件
defaults write com.apple.finder AppleShowAllFiles -bool YES
killall Finder

# 取消显示所有隐藏文件
defaults write com.apple.finder AppleShowAllFiles -bool NO
killall Finder
```

## 视频格式转换

```
# 查看ffmpeg的安装选项，可以按照你自己的要求选装
brew info ffmpeg

# 安装FFmpeg
brew install ffmpeg --with-fdk-aac --without-faac

#列出支持的编解码器
ffmpeg -codecs

#列出支持的滤镜
ffmpeg -filters

#列出支持的格式
ffmpeg -formats

# 把光驱DVD格式文件转成MP4格式
cat VIDEO_TS.VOB VTS_01_0.VOB VTS_01_1.VOB VTS_01_2.VOB | ffmpeg -i - ~/mika_01.mp4

# 抽取flv视频中的音频
ffmpeg -i INPUT.flv -acodec libmp3lame -ab 128k OUTPUT.mp3

# 把AVI格式转换成MP4格式
ffmpeg -i INPUT.avi -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 OUTPUT.mp4 
```
