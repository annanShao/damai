# 大麦网抢票脚本

基于 [AnTi-anti/damai_ticket](https://github.com/AnTi-anti/damai_ticket) 开源版本进行修改

> 2023.03.04 修改使抢票脚本对部分演唱会有效
> 
> 2023.03.20 对应页面更新了class_name, 但是出现新机制触发机器验证无法完成下单
>
>
> 2023.03.23 感谢 @wuliang9524 提供的解决方案, 需要修改chromedriver以隐藏爬虫标志
> 
> This repo is forked from [here](https://github.com/838239178/damai_tickets)
> 
> 🚩**Disclaimer:
The following code provided is intended for educational and informational purposes only. The code is provided "as is" without any warranties or guarantees of any kind, either expressed or implied. The author and the provider of this code shall not be held responsible for any damages or liabilities arising from the use or misuse of the code. The user of this code assumes all responsibility and risk for its use. It is recommended to thoroughly review and test the code before implementing it in any production or critical systems. The author disclaims any responsibility for errors, inaccuracies, or omissions in the code or the consequences that may arise from them. By using this code, you agree to these terms and conditions.**

## Chromedriver 修改 （目前已经修改过 73 版本的驱动已经放在 repo 里边了，需要做的就是降级自己的 chrome 「from annanShao」）

1. 下载Hexedit或者使用Vscode中的Hexedit插件
2. 使用Hexedit打开chromedriver.exe 
3. 搜索 `$cdc_`
4. 更改为任意其他字符串，如`$cxx_`


## 配置文件

```json
{
    "date": [1],
    "sess": [1],
    "price": [2],	
    "real_name": [1],
    "nick_name": "",
    "ticket_num": 3,
    "driver_path": "./chromedriver.exe",
    "damai_url": "https://www.damai.cn/",
    "target_url": "https://m.damai.cn/damai/detail/item.html?itemId=704494827883&spm=a2o71.category.itemlist.ditem_3"
}

```

- target_url 抢票的网页，必须是移动端网页，即m.damai.cn域名下的网页。
- damai_url 一般不需要更改，用于登录
- ticket_num 抢票张数
- date 日期 这个版本未测试包含日期筛选的网页，目前大概率不可用，一般来说也不太用得到
- sess 场次，对应买票页面弹框的场次，1代表第一个按钮，数组表示多个可选项
- price 价位，对应买票页面弹框的价格，1代表第一个按钮，数组表示多个可选
- driver_path 对应当前电脑Chrome浏览器版本的驱动文件
- real_name 结算页面选择第几个实名的人
- nick_name 没什么用

## 注意事项

1. 账号必须先做好实名制认证，并添加至少一个实名制的人的信息
2. 第一次打开后会进入登录页面，需要手动选择扫码登陆
3. 如果太久没用，需要先清空目录下的 cookie 文件，然后在重新登录
