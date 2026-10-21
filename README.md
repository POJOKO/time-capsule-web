# 时间胶囊 Time Capsule

本地加密、到期才能解锁的回忆网页，支持跨设备同步。

## 在线访问

https://pojoko.github.io/time-capsule-web/

## 功能

- **存入回忆**：标题 + 正文 + 照片/视频，设定多少天后可查看，用解锁密码加密（浏览器 WebCrypto，PBKDF2 + AES-256-GCM）。
- **到期解锁**：未到期只能看到还剩几天，到期后输入解锁密码查看全文与图片。
- **跨设备同步**：在每台设备填同一段「同步口令」，彼此的胶囊会自动合并到一起。

## 隐私说明

- 正文与媒体在**你的浏览器里加密**后才上传，服务器（Supabase）里只有密文、时间戳和一个由口令散列出的空间 ID。
- 解锁密码不会上传，丢失后无法恢复。
- 同步口令不上传，只上传它的 SHA-256 散列，用来区分不同人的数据空间。
- 云端只有「读取」和「新增」权限，没有修改/删除权限，所以在线数据不会被别人改写或清空。

## 同步后端

- 服务：Supabase（免费额度）
- 项目地址：`https://kqdrivwvzlyptxyykujt.supabase.co`
- 数据表：`capsules(id text pk, created_at timestamptz, space_id text, payload text)`
- 访问策略：`SELECT` 与 `INSERT` 对 `public` 开放（匿名 key），`UPDATE`/`DELETE` 未开放
- 页面里内置的是 publishable（匿名）key，可以公开；**secret key 没有也不会放进网页**

> 免费项目若连续 7 天无人访问会被自动暂停，打开一次网页（或后台点一次 Sync）即可恢复。

## 更新网页

GitHub 网页里打开本仓库 → Add file → Upload files → 把新的 `index.html` 拖进去 → Commit changes。
约 1 分钟后刷新在线地址即可看到更新。
