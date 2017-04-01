一个用openresty（nginx+lua）做认证拦截校验的概念原型
# 安装运行
其实按官网来就好了
## 安装openresty
``` 
sudo yum-config-manager --add-repo https://openresty.org/yum/centos/OpenResty.repo
```
or
``` 
sudo yum-config-manager --add-repo https://openresty.org/yum/cn/centos/OpenResty.repo
```
then
```
sudo yum install openresty -y
```
## 运行
```
openresty -p `pwd`/ -c conf/nginx.conf 
```

## 测试
交替

```
curl http://localhost:8080 -I
```
显示200或403

## 说明
其实也没什么好说明的，就是设了一共享变量，然后每请求一次加1，奇数或偶数校验接口返回403或200，然后lua根据这个结果决定是不是放行proxy_pass
