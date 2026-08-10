# balance_BVC-autoyuanqin-scores

个人 BetterGI AutoYuanQin（原神自动弹琴）脚本与曲谱仓库。

## 目录结构

```
repo/
└── js/
    └── AutoYuanQin/            ← 完整 AutoYuanQin 脚本（官方 3.7.6 + 个人曲谱）
        ├── main.js
        ├── manifest.json
        ├── settings.json
        ├── README.md
        └── assets/
            ├── score_file/     ← 个人曲谱都放在这里（aLIEz.json 等）
            ├── tutorial_file/  ← 官方制谱器（MIDI / 五线谱 / 简谱）
            ├── index.html      ← 游戏内控制面板
            └── instruments/    ← 乐器图标
repo.json                       ← BetterGI 脚本仓库索引
README.md
```

## 在 BetterGI 中使用

1. 打开 BetterGI → 全自动 → 脚本仓库 → 设置，渠道选择「自定义」。
2. 填写：
   - 仓库地址：`https://github.com/balance-BVC/balance_BVC-autoyuanqin-scores.git`
   - 用户名称：`balance-BVC`
   - 访问令牌：公开仓库可留空；如需填写，请使用 GitHub Personal Access Token（不是登录密码）
3. 点击「更新仓库」，等待完成。
4. 在 Javascript脚本 目录下找到 AutoYuanQin 并订阅，之后即可在调度器中使用。

## 如何添加自己的曲谱

1. 使用 `repo/js/AutoYuanQin/assets/tutorial_file/` 下的制谱器生成 JSON，或手写 `keyboard` 类型键盘谱。
2. 放入 `repo/js/AutoYuanQin/assets/score_file/`，确保 JSON 的 `name` 与文件名一致。
3. 在本地 BetterGI 中运行一遍 AutoYuanQin 脚本（打开原神并进入乐器界面），脚本会自动更新 `settings.json`。
4. 提交并推送（BetterGI 固定读取 `release` 分支，两个分支都要同步）：

```bash
git add .
git commit -m "添加曲谱：曲名"
git push
git push origin release
```

## JSON 字段说明（简版）

| 字段 | 必填 | 说明 |
| --- | --- | --- |
| `name` | 是 | 曲名，需与文件名一致 |
| `type` | 是 | 曲谱类型：`yuanqin` / `midi` / `keyboard` |
| `bpm` | 是 | 演奏速度 |
| `time_signature` | yuanqin 类型必填 | 拍号，例如 `4/4` |
| `notes` | 是 | 曲谱内容 |
| `author` | 否 | 录谱人（建议填写） |
| `instrument` / `composer` / `arranger` / `description` | 否 | 可选元信息 |

详细格式请参考脚本目录内的 `README.md` 与 `assets/tutorial_file/example.json`。

## 说明

- AutoYuanQin 脚本本体来自官方 [babalae/bettergi-scripts-list](https://github.com/babalae/bettergi-scripts-list)（`repo/js/AutoYuanQin`），本仓库在此基础上维护个人曲谱。
- 本仓库有两个分支：`main`（源码/默认分支）与 `release`（BetterGI 实际读取的分支）。
