演示http://ecshop.liangsonghua.me/
账号songhuapidan@gmail.cpm密码rootroot
后台http://ecshop.liangsonghua.me/admin/login/login
账号root密码rootroot
天数：12天。
使用的技术：ThinkPHP3.2.1
功能模块：
1.	商品模块
  a)	商品分类（无限级分类）
  b)	商品类型（商品是什么东西：书、电脑、文化用品）
    i.	商品属性（不同类型的商品有不同的属性，如书有：出版社、作者等等）
  c)	商品图片
  d)	库存量：保存一件商品所有属性组合之后的数量，如：白色+4G， 黑色+5G多少等等。
  e)	会员价格：不同的会员级别单独设置一个价格
  f)	评论
2.	会员模块
  a)	会员级别管理：指定某积分范围是哪个级别
  b)	会员管理
3.	定单模块

商品表模块需求分析：
1.	商品表的管理包括：CRUD、搜索、排序、翻页
2.	考虑到SQL注入、XSS
3.	使用JS插件：时间插件、在线编辑器
管理员登陆模块需求分析：
1.	项目中有一个超级管理员（root/admin），拥有所有的权限，这个账号是不允许删除的
2.	每个管理员有一个是否启用的状态，如果禁用了就不能登录
3.	登录时需要有验证码
4.	只有登录的管理员才能访问后台
权限模块需求分析：
1.	权限管理（无限级） 【一个权限可以被多个角色拥有】
2.	角色管理（可以把权限分配给这个角色）【一个角色可以拥有多个权限】【一个角色可以有多个管理员】
3.	管理员管理（可以指定管理员属于哪些角色）【一个管理员可以同时属于多个角色】
4.	后台左侧只显示当前登录的管理员有权限访问的按钮
5.	超级管理员（id=1）拥有所有页面，普通管理员只能访问分配了权限的页面
管理员模块分析：
1.	管理员的账号添加一个验证规则：必须唯一
2.	添加管理员时添加一个确认密码，只有两个密码输入一致时才可以添加
3.	添加管理员时把密码加密之后存到数据库中
4.	修改管理员时和添加管理员一样也要有前三个需求，如果密码不填就代表不修改密码
5.	在添加修改管理员时，可以选择管理员所在的角色（可以选择多个角色）
6.	删除管理员时，要把这个管理员所在角色的数据一起删除掉
7.	超级管理员是不能被禁用和删除的
8.	超级管理员可以修改所有的管理员的信息，但普通管理员只能修改自己的信息
商品模块需求分析：
1.	商品类型管理
   a)	属性管理（属性分为唯一属性和单选属性两种、基本中如果是唯一属性，在添加商品时是一个文本框，如果是单选属性属性前面要有一个+号）：
2.	商品分类的管理
3.	商品管理
4.	会员模块：
 会员级别管理
  会员价格
    1. 会员级别管理
   2. 为一件商品为每个级别都指定一个价格
5.商品相册
  商品和图片什么关系？
   一个商品有多个图片，每件商品只属于这一件商品所以是一对多
6.商品属性的
  商品和属性是什么关系？
  一个商品可以有多个属性。
  一个属性可以被多个商品拥有。
7.商品库存量


商品基本信息
商品名称、价格、所在主分类、所在副分类（可以属于多个副分类）等等
会员价格（每个会员级别要设置一个价格）
商品相册
商品所在类型和属性
商品库存量管理（商品所拥有的可选的属性可组合起来添加库存量）

类型模块分析：
1.	类型的CRUD
2.	在类型的列表页中添加一个属性列表的按钮，点击之后进入这个类型下所有属性的列表页
3.	属性的CRUD
4.	在属性列表中上面有一个类型的下拉框，一选择类型就可以切换到相应类型的属性列表中
购物车模块分析
1.	当会员没有登录时，添加购物车时，把购物车中的数据存到COOKIE(如果存到SESSION中，那么效果就是关闭浏览器之后购物车中的数据就清空了)中
2.	一旦会员登录之后就把购物车中的数据转移到数据库中，清空COOKIE





