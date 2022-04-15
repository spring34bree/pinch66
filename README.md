[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://dashboard.heroku.com/new?template=https://github.com/spring34bree/pinch66)

### 路径

`WebSocket` 路径(配置文件中的 `path` )为 `/` 。

### 端口

`端口` 为 `443` 。

### UUID

`UUID` 默认为 `24b4b1e1-7a89-45f6-858c-242cf53b5bdb` 可自行设置。

**XRay 将在部署时会自动实配安装`最新版本`。**

**出于安全考量，除非使用 CDN，否则请不要使用自定义域名，而使用 Heroku 分配的二级域名，以实现 XRay vless Websocket + TLS。**

## 流量中转

<details>
<summary>可以使用cloudflare的workers来中转流量，配置为：  </summary>

```js
addEventListener(  
    "fetch",event => {  
        let url=new URL(event.request.url);  
        url.hostname="xxx.herokuapp.com";//你的heroku域名    
        let request=new Request(url,event.request);  
        event. respondWith(  
            fetch(request)  
        )  
    }  
)  
