
# 1.生成package


```
cd ~
workon thap
mkdir packages
cd packages
pip freeze > requirements.txt
pip install --download ./ -r requirement.txt
cd ..
tar zcvf packages.tar.gz packages/
```

# 2.将package拷贝到新电脑

```
apt-get update
apt-get install python-setuptools
tar zxvf packages.tar.gz
cd packages
pip install virtualenvwrapper-4.8.2-py2.py3-none-any.whl --no-index --find-links=./
mkdir $HOME/.virtualenvs
sed -i '$aexport WORKON_HOME=$HOME/.virtualenvs' /root/.bashrc
sed -i '$asource /usr/local/bin/virtualenvwrapper.sh' /root/.bashrc
source /root/.bashrc
mkvirtualenv -p /usr/bin/python3 thap
pip install -r requirements.txt --no-index --find-links=./
```

