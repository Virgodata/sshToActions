# SSH to GitHub Actions

This GitHub Action offers you connect to GitHub Actions VM via SSH for interactive debugging（这个 Action 让你通过 SSH 连接到 GitHub Actions虚拟机进行交互式调试）

## Features

- Support Ubuntu and macOS（支持 Ubuntu 和 macOS）
- Provides two optional SSH connection methods, tmate and ngrok（提供 tmate 和 ngrok 两种可选 SSH 连接方式）
- Proceed to the next step to stay connected（继续下一步以保持连接）
- Send SSH connection info to Telegram（将 SSH 连接信息发送到 Telegram）

## Usage

### Connect to Github Actions VM via SSH by using（使用 SSH 连接到 Github Actions虚拟机） [tmate](https://tmate.io)

```yaml
- name: Start SSH via tmate
  uses: Virgodata/sshToActions@main
  # Send connection info to Telegram (optional)
  # You can find related documents here: https://core.telegram.org/bots
  env:
    TELEGRAM_BOT_TOKEN: ${{ secrets.TELEGRAM_BOT_TOKEN }}
    TELEGRAM_CHAT_ID: ${{ secrets.TELEGRAM_CHAT_ID }}
```

### Connect to Github Actions VM via SSH by using（使用 SSH 连接到 Github Actions虚拟机） [ngrok](https://ngrok.com)

```yaml
- name: Start SSH via ngrok
  uses: Virgodata/sshToActions@main
  with:
    mode: ngrok
  env:
    # After sign up on the https://ngrok.com
    # You can find this token here: https://dashboard.ngrok.com/auth/your-authtoken
    NGROK_TOKEN: ${{ secrets.NGROK_TOKEN }}
    
    # ngrok server region [us, eu, au, ap, sa, jp, in] (optional, default: us)
    # You can find this server region here: https://ngrok.com/docs#global-locations
    NGROK_REGION: us

    # This password you will use when authorizing via SSH
    SSH_PASSWORD: ${{ secrets.SSH_PASSWORD }}

    # Send connection info to Telegram (optional)
    # You can find related documents here: https://core.telegram.org/bots
    TELEGRAM_BOT_TOKEN: ${{ secrets.TELEGRAM_BOT_TOKEN }}
    TELEGRAM_CHAT_ID: ${{ secrets.TELEGRAM_CHAT_ID }}
```

## Lisence

[MIT](https://github.com/P3TERX/ssh2actions/blob/main/LICENSE) © P3TERX
