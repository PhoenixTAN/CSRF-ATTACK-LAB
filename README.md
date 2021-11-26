# CSRF-ATTACK-LAB
CSRF attack simulation.

## 如何发动
1. 网站A域名为www.asite.com（模拟正常网站）
2. 网站B域名为www.bsite.com (模拟想要实施攻击的网站)
3. 同一个浏览器中，用户在网站A进行了登录，登录信息都存在cookie. 并且，用户也打开了网站B.
4. 网站A提交表单的操作会触发请求https://www.asite.com/post并且带上了该域名的cookie.
5. 如果在网站B的某个按钮，点击的时候发送请求https://www.asite.com/post， 这会带上网站A域名下的cookie,从而成功通过网站A服务器的鉴权。

## 防范措施

### 初级 -- 验证referrer
服务器要去鉴定请求头的referrer 其实这个referrer是不是postman就可以伪造。
### 高级 -- 验证csrf-token
每次进入页面 前端都找服务器要一个csrf-token 存在内存里 不能存在cookie 每一个请求都带上csrf- token给服务器，服务器来验证这个token.
