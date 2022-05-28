## API接口文档

### api路径总览

- api/admin/
- api/user/
  - login/email 邮箱登陆
  - login/phone 手机登陆	
  - login/vercode_p 发送手机验证码
  - login/vercode_e 发送邮箱验证码
  - login/phone     手机+密码登陆
  - logout    登出
  - message_get  获取用户个人信息
  - message_set 设置用户个人信息
  - password_set 修改密码
  - register_e 邮箱注册
  - register_p 手机号注册
- api/book/
  - message_get 获取某个图书全部信息
  - message_set 设置图书全部信息
  - listBook 列出评分最高的几个图书信息
  - insertImg 插入图书图片（先不用）
  - uploadImg 上传图书图片
  - getImg 查询图书图片
- api/movie/
  - message_set
  - message_get
  - listmovie 
  - moviesearch 根据关键词查找电影
  - imgupload 图片
  - getimg 图片

- api/mark/
  - addmark 添加评论
  - getmark 返回评论
  - thumb 点赞

- api/group/
- api/topic/
- api/search/

### api接口详情

## 用户登陆注册、修改个人信息

|     条目     |                             内容                             |
| :----------: | :----------------------------------------------------------: |
|     编号     |                             101                              |
|   api路径    |                        api/user/login                        |
|   请求方式   |                             POST                             |
| 携带数据示例 | `{"username":"Tom", "password":"123456"}`<br />`{"username":"12345@qq.com","password":"123456"}` |
| 返回数据示例 | `{"success":true, "message":"登陆成功","username":"Tom"}`<br />`{"success": false, "message":"用户名或邮箱不存在"}`<br />`{"success": false,"message":"密码错误"}` |
|     说明     |                       邮箱或用户名登陆                       |
|   实现情况   |                                                              |

|     条目     |                             内容                             |
| :----------: | :----------------------------------------------------------: |
|     编号     |                            101-1                             |
|   api路径    |                       api/user/logout                        |
|   请求方式   |                             POST                             |
| 携带数据示例 |   `{"username":"Tom"}`<br />`{"username":"12345@qq.com"}`    |
| 返回数据示例 | `{"success":true, "message":"注销成功"}`<br />`{"success":false, "message":"注销失败"}` |
|     说明     |                       邮箱或用户名登陆                       |
|   实现情况   |                                                              |

|     条目     |                             内容                             |
| :----------: | :----------------------------------------------------------: |
|     编号     |                             102                              |
|   api路径    |                   api/user/login/vercode_p                   |
|   请求方式   |                             GET                              |
| 携带数据示例 |               `{"phoneNumber":"18811591037"}`                |
| 返回数据示例 | `{"success":true,"message":"验证码已发送","username":"Tom"}`<br />`{"success": false, "message":"验证码发送失败"}` |
|     说明     |                       获取手机号验证码                       |
|   实现情况   |                                                              |

|     条目     |                             内容                             |
| :----------: | :----------------------------------------------------------: |
|     编号     |                             103                              |
|   api路径    |                     api/user/login/phone                     |
|   请求方式   |                             POST                             |
| 携带数据示例 |     `{"phoneNumber":"18811591037"，"vercode":"123456"}`      |
| 返回数据示例 | `{"success":true,"username":"Tom"}`<br />`{"success": false, "message":"验证码错误"}` |
|     说明     |                   检查验证码是否正确并登陆                   |
|   实现情况   |                                                              |

|     条目     |                             内容                             |
| :----------: | :----------------------------------------------------------: |
|     编号     |                             104                              |
|   api路径    |                  api/user/login/register_e                   |
|   请求方式   |                             POST                             |
| 携带数据示例 | `{"email":"18811591037@qq.com"，"username":"Tom Fuck",vercode":"123456"}` |
| 返回数据示例 | `{"success":true,"username":"Tom"}`<br />`{"success":false, "message":"验证码错误"}`<br />`{"success":false, "message":"用户名已存在"}`<br />`{"success":false, "message":"邮箱已注册"} |
|     说明     |                        验证邮箱并注册                        |
|   实现情况   |                                                              |

|     条目     |                             内容                             |
| :----------: | :----------------------------------------------------------: |
|     编号     |                             105                              |
|   api路径    |                  api/user/login/register_p                   |
|   请求方式   |                             POST                             |
| 携带数据示例 | `{"phoneNumber":"18811591037"，"username":"Tom Fuck",vercode":"123456"}` |
| 返回数据示例 | `{"success":true,"username":"Tom Fuck"}`<br />`{"success":false, "message":"手机号已注册"}`<br />`{"success":false, "message":"用户名已存在"}`<br />`{"success":false, "message":"验证码不正确"}` |
|     说明     |                       验证手机号并注册                       |
|   实现情况   |                                                              |

|     条目     |                             内容                             |
| :----------: | :----------------------------------------------------------: |
|     编号     |                             106                              |
|   api路径    |                   api/user/login/vercode_e                   |
|   请求方式   |                             GET                              |
| 携带数据示例 |               `{"email":"18811591037@qq.com"}`               |
| 返回数据示例 | `{"success":true,"message":"验证码已发送"}`<br />`{"success": false, "message":"验证码发送失败"}`<br />`{"success": false, "message":"邮箱不存在"}` |
|     说明     |                        获取邮箱验证码                        |
|   实现情况   |                                                              |

|     条目     |                             内容                             |
| :----------: | :----------------------------------------------------------: |
|     编号     |                             107                              |
|   api路径    |                  api/user/login/message_get                  |
|   请求方式   |                             GET                              |
| 携带数据示例 |                     `{"username":"Tom"}`                     |
| 返回数据示例 | form: {<br/>          name: '',<br/>          password: '',<br/>          regionOP: '',<br/>          date1: '',<br/>          birthOP: '',<br/>          email: '',<br/>          phone: '',<br/>          region1: [ ],<br/>          region2: [ ]<br/>        } |
|     说明     |                         获取个人信息                         |
|   实现情况   |                                                              |

|     条目     |                             内容                             |
| :----------: | :----------------------------------------------------------: |
|     编号     |                             108                              |
|   api路径    |                  api/user/login/message_set                  |
|   请求方式   |                             POST                             |
| 携带数据示例 | form: {<br/>          name: '',<br/>          password: '',<br/>          regionOP: '',<br/>          date1: '',<br/>          birthOP: '',<br/>          email: '',<br/>          phone: '',<br/>          region1: [ ],<br/>          region2: [ ]<br/>        } |
| 返回数据示例 | `{"success":true, "message":"成功获取"}`<br />`{"success":false, "message":"获取失败"}` |
|     说明     |                         获取个人信息                         |
|   实现情况   |                                                              |
