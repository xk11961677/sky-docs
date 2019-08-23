# 生成秘钥
ssh-keygen -t rsa -C "shen11961677@163.com"


ssh-keygen -t rsa -C "liwei.shen@company-core.com"


# 增加config文件 在~/.ssh目录下
### github
Host github
HostName github.com
User git
IdentityFile ~/.ssh/id_rsa_github
### gitlab(公司)
Host gitlab
HostName code.doooly.cn
User git
IdentityFile ~/.ssh/id_rsa_github_reach

# 检查git默认配置
git config --list

# 设置git全局用户
git config --global user.name 'shen11961677@163.com'
git config --global user.email 'shen11961677@163.com'

# 设置局部用户
git config --local user.name 'shenliwei'
git config --local user.email 'liwei.shen@company-core.com'

# 使用时,需要修改对应host
比如: git@github.com:xk11961677/skycloud-base.git
修改: git@github:xk11961677/skycloud-base.git

# idea 使用
git客户端clone后,在对应仓库执行 `设置局部用户`
