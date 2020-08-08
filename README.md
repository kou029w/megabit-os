# Yama

Raspberry Pi 向け OS のビルドするためのツール群

- Alpine Linux ベース (armhf)
- WiFi 対応
- その他オレオレカスタマイズ

## ビルド

```sh
bin/build
```

### SD カードのフォーマット

- FAT32 (LBA)
- boot フラグ付ける
- ボリュームラベル付けない

### SD カードに書き込み

```sh
rsync -a dist/ /path/to/sd/
```

### 前提条件

- Docker Compose
- curl
- grep
- jq
- ruby
- ssh-keygen
- bash
- qemu-user-static

### WiFi の設定

`apkovl/etc/wpa_supplicant/wpa_supplicant.conf` 配置後ビルド

```sh
bin/conf-gen | tee apkovl/etc/wpa_supplicant/wpa_supplicant.conf
```

### ssh の設定

`apkovl/root/.ssh/authorized_keys` をパーミッション 600 で配置後ビルド
