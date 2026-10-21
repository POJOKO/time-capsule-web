# 时间胶囊 Time Capsule

本地加密、到期才能解锁的回忆网页。

## 在线访问

https://pojoko.github.io/time-capsule-web/

## 说明

- 内容使用浏览器 WebCrypto 的 AES-GCM 加密，密码只在你输入时使用，不会保存。
- 加密后的数据存在**你自己设备的浏览器**里（IndexedDB），不会上传到 GitHub 或任何服务器。
- 因此：换设备、换浏览器、清理浏览器数据都会看不到原来的胶囊；网址本身只是网页入口。

## 更新网页

在 GitHub 网页里打开本仓库 → Add file → Upload files → 把新的 `index.html` 拖进去 → Commit changes。
一两分钟后刷新在线地址即可看到更新。
