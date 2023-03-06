## Failed to connect to github.com port 443: Connection refused问题解决

```bash
// 关闭代理
git config --global --unset http.proxy
git config --global --unset https.proxy

// 添加全局代理
git config --global http.proxy
git config --global https.proxy
```

