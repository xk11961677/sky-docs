# 生成秘钥
ssh-keygen -t rsa -C "shen11961677@163.com"


ssh-keygen -t rsa -C "liwei.shen@company-core.com"

# 将生成的公钥分别放入git与gitlab的setting选项

# 增加config文件 在~/.ssh目录下
####### github
Host github</br>
HostName github.com</br>
User git</br>
IdentityFile ~/.ssh/id_rsa_github</br>
####### gitlab(公司)
Host gitlab</br>
HostName code.doooly.cn</br>
User git</br>
IdentityFile ~/.ssh/id_rsa_github_reach</br>

# 检查git默认配置
git config --list

# 设置git全局用户
git config --global user.name 'shen11961677@163.com'</br>
git config --global user.email 'shen11961677@163.com'</br>

# 设置局部用户
git config --local user.name 'shenliwei'</br>
git config --local user.email 'liwei.shen@company-core.com'</br>

# clone时修改对应host
比如: git@github.com:xk11961677/skycloud-base.git</br>
修改: git@github:xk11961677/skycloud-base.git</br>

# idea 使用
git客户端clone后,在对应仓库执行 `设置局部用户`
