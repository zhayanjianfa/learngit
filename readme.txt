# 测试将本地仓库推送到GitHub上的空仓库

这里我先将本地仓库的名字设置成和github上创建的仓库名一样：learngit

这里碰到了几个问题，先简单记录：
1.执行“git push -u origin main”时出现错误：

> remote: Permission to zhayanjianfa/learngit.git denied to jackking2015.

这里我参考网上的解决方法，删除Windows凭据里有关github的所有账号。
2.解决上面问题后，继续执行上面的操作，仍然报错：

> fatal: 发送请求时出错。
> fatal: 无法连接到远程服务器
> fatal: 由于连接方在一段时间后没有正确答复或连接的主机没有反应，连接尝试失败。 20.205.243.166:443
> zerror: unable to read askpass response from 'C:/Program Files (x86)/Git/mingw32/bin/git-askpass.exe'
> Username for 'https://github.com': zhayanjianfa
> remote: Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.
> remote: Please see https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/ for more information.
> fatal: Authentication failed for 'https://github.com/zhayanjianfa/learngit.git/'

​	这里我猜测是网络的原因，所以用上了v2ary，后面运行正常。

3.还有一个疑惑的地方就是，这里最开始设置的全局用户名和邮箱，根据《github入门与实践》提醒是在提交代码时会附带上的，所以我猜测可能只是一个昵称。
然后后续在执行“ssh-keygen -t rsa -C "yourmail@example.com"”里的邮箱却要设置成和github上一样，我开始猜测是不是一种证明是同一用户的含义？？？所以后面要输入密码时，我就输入了github的密码。后来我越想越糊涂，觉得不一定是，因为我执行"git push -u origin main"时，要求我输入github密码，并确认与我本地互通，所以我猜测本地输入的密码只是一个本地的账户？？？

4.还有我本地的仓库名一定要和github上准备推送的仓库门一致吗？64位的git和32位git的设置选项好像有些不同，如果本地的主线是master，推送上去会是什么样？git push -u origin main究竟是什么意思？为什么推送到空项目时，github没有收到pull request消息？是因为账号一致吗？还是因为不同操作？

5.我最后发现github上显示推送的账户竟然是jackking2015，我猜测还是因为我前面设置全局邮箱有关，尽管我设置的用户名是bender，但它可能还是采用了邮箱注册的github用户名。这个需要进一步验证。

​	这里我用git config --global user.email "***"方式更改了邮箱，再测试一下，看看是谁在推送！

最后验证了我的猜想，但如果用的邮箱是一个没有注册过的邮箱，估计，最后显示的名字就是本地设置的名字。所以我猜测本地设的密码也是本地用的，和github毫无关系。



6.参考书本，为了弄个头像，注册了gravatar，但没时间继续弄，后续再研究。



7.我猜测这种拉取代码到本地可能只是工作方式的一种，更多的可能是fork形式，然后请求合并之类的。明天再研究吧。



8.没有v2ary上传不了代码，有了也时常会上传失败，这是个问题，如果代码量多，更是个问题。有机会看看别人怎么解决的。

9.怎么一步到位git add ,git commit ,git push?

10.多个文件时，要一直git add多个文件吗？这对大型项目其实有点不便的。有什么解决方法，后续研究下。