I have downloaded these e-books.

github生成SSH 密钥步骤 详情
修改自己项目的配置件

编辑项目目录下的.git/config件
找到:

[remote "origin"]
    url =https://github.com/hit9/hit9.github.com.git
        fetch = +refs/heads/*:refs/remotes/origin/*

	把url处改成ssh地址:

	[remote "origin"]
	    url =git@github.com:hit9/hit9.github.com.git
	        fetch = +refs/heads/*:refs/remotes/origin/*

		url是 https的时候会采用用户名认证. 是ssh地址的时候才会采用ssh认证

		这样每次push就不用输入账号密码了……

