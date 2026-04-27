# NTE Auto Sign（塔吉多 / 异环）

用于塔吉多社区异环游戏自动签到，支持多账号管理、手动切换和 EXE 打包。

## 功能

- 手机号 + 短信验证码登录
- `refreshToken` 登录（高级模式）
- 多账号保存到 `TOKEN.txt`（每行一个账号）
- 运行时手动选择账号（单选/多选/全部）
- 社区签到 + 游戏签到
- 输出“今日道具”到终端和日志
- 日志脱敏并精简输出（`logs\YYYY-MM-DD.log`）

## 快速开始（Python）

1. 安装依赖

```bash
pip install -r requirements.txt
```

2. 添加账号（可连续添加多个）

```bash
python add_account.py
```

3. 执行签到

```bash
python nte.py
```

## 账号文件 `TOKEN.txt`

每行一个账号，推荐 JSON 格式：

```json
{"refreshToken":"xxx","uid":"10xxxx","deviceId":"xxxxx","gameId":"1289","roleIds":["2160xxxxxxx"]}
```

## 多账号选择

当 `TOKEN.txt` 中有多个账号时，`nte.py` 会提示选择：

- `1`：只签到第 1 个账号
- `1,3`：签到第 1 和第 3 个账号
- 回车 / `all` / `a`：签到全部账号

## EXE 构建与使用（Windows）

构建（无 Python 环境推荐使用）：

```bat
.\.build\build_exe.bat
```

产物目录：`dist\windows\`

- `nte.exe`：签到主程序
- `add_account.exe`：添加账号工具

说明：直接双击 `nte.exe`、`add_account.exe` 即可运行。

## 环境变量

| 变量 | 说明 |
| --- | --- |
| `TOKEN` | 账号信息（支持多行，格式同 `TOKEN.txt`） |
| `TGD_GAME_ID` | 默认游戏 ID（默认 `1289`） |
| `TGD_ROLE_IDS` | 角色 ID（逗号分隔，补充/覆盖自动拉取） |
| `TGD_SIGN_GAME_IDS` | 签到时尝试的 gameId 列表（逗号分隔） |
| `EXIT_WHEN_FAIL=on` | 任一账号失败时，进程退出码为 1 |
| `NO_PAUSE=1` | Windows 下失败时不等待回车 |
| `SKYLAND_TYPE=add_account` | 仅添加账号，不执行签到（一般建议直接用 `add_account.py`） |

## 常见问题

- `refreshToken 已失效`：删除 `TOKEN.txt` 重新登录添加账号即可。

## 致谢

本项目由 skyland-auto-sign 开源项目修改完成：  
https://gitee.com/FancyCabbage/skyland-auto-sign

## 演示图片

![演示图 1](assets/1.png)

![演示图 2](assets/2.png)

![演示图 3](assets/3.png)
