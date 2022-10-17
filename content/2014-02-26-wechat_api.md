---
title: WeChat API
date: 2014-02-26
---
#### The WeChat API

Last night I made a little bit of an effort to tinker with the WeChat API, for it seems there are many interesting things one can do with it. And since it is one of the biggest way of marketing oneself on earth. It turned out to be quite necessary that I know how to program with the WeChat API.

#### Two kinds of Accounts

There are two kinds of **WeChat Public Accounts** (At least that's how they call them), the Service Account and the Subscription Account. Service Accounts are for corporations, and other commercial entities, in-app menus and other features comes directly in the package with **Service Accounts**, and also, Service Account users can only broadcast messages once a month. Subscription Accounts, on the other hand, do not come with all the fancy features, including the in-app menus, perchases, and so on. However, if a user pays **300 RMB** per year, the Subscription Account can also enjoy what the Service Accounts do. It all depends on to what extent a user want to do with this publicity after all.

#### Functions

All users will gain the WeChat API after they specify their addresses, what they do and upload a legit logo. Basic API functionalities are as follows:

*   Broadcasting Messages
*   Receiving Messages
*   Auto Reply

It seems to be quite simple, but in fact, there are a few types of messages:

*   Text Messages
*   GeoLocation Messages
*   Video Messages
*   Voice Messages
*   Graphic Messages

Now it is quite clear isn't it ? WeChat Account managers can utilize all kinds of informations on this platform, including user data, geographic informations to precisely market their products, interact with users programmatically.

#### Techonology

I tried to use some existing libraries:

*   [PHP Library](http://sae.sina.com.cn/?m=apps&a=detail&aid=162)
*   [Python](http://kingson.org/?p=259)

But finally, I tried to do it on my own:

\# coding: UTF-8
import os

import sae
import web

web.config.debug \= True

from wxAPI import WeixinInterface

urls \= (
    '/', 'Hello',
    '/weixin','WeixinInterface'
)

app\_root \= os.path.dirname(\_\_file\_\_)
templates\_root \= os.path.join(app\_root, 'templates')
render \= web.template.render(templates\_root)

class Hello:
    def GET(self):
        return render.hello("你好")

app \= web.application(urls, globals()).wsgifunc()

application \= sae.create\_wsgi\_app(app)

Let's see what we can do here.

