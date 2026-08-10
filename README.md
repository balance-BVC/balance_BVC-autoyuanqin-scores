# balance_BVC-autoyuanqin-scores

个人 AutoYuanQin（原神自动弹琴）曲谱仓库。

## 目录结构

```
AutoYuanQin/
└── assets/
    ├── score_file/        ← 曲谱 JSON 都放在这里
    │   └── Bad Apple - xvgqEYdD.json（示例曲谱）
    └── tutorial_file/
        └── example.json   ← 官方格式参考（五线谱/简谱制谱器格式）
```

## 如何添加自己的曲谱

1. 制谱：使用官方 [AutoYuanQin](https://github.com/babalae/bettergi-scripts-list/tree/main/repo/js/AutoYuanQin) 仓库中的 **MIDI 制谱器 / 五线谱制谱器 / 简谱制谱器** 生成 JSON，或手写 `keyboard` 类型键盘谱。
2. 检查：JSON 中 `name` 字段必须与文件名一致（脚本运行时会自动重命名为「曲名-8位hash」格式）。
3. 放入 `AutoYuanQin/assets/score_file/` 目录。
4. 在 BetterGI 中运行一遍 AutoYuanQin 脚本（需要打开原神并进入乐器界面），脚本会自动更新 `settings.json`，确认左下角日志显示更新成功。
5. 提交并推送：

```bash
git add .
git commit -m "添加曲谱：曲名"
git push
```

## 如何演奏

把本仓库 `AutoYuanQin/assets/score_file/` 下的 JSON 复制到本地 BetterGI 的 AutoYuanQin 脚本目录（`AutoYuanQin/assets/score_file/`）中，运行脚本即可。也可以直接把这个仓库作为 AutoYuanQin 脚本的目录来使用。

## JSON 字段说明（简版）

| 字段 | 必填 | 说明 |
| --- | --- | --- |
| `name` | 是 | 曲名，需与文件名一致 |
| `type` | 是 | 曲谱类型：`yuanqin`（五线谱/简谱制谱器）、`midi`（MIDI 制谱器）、`keyboard`（网络琴谱） |
| `bpm` | 是 | 演奏速度（Beats Per Minute） |
| `time_signature` | yuanqin 类型必填 | 拍号，例如 `4/4` |
| `notes` | 是 | 曲谱内容 |
| `author` | 否 | 录谱人（建议填写） |
| `instrument` / `composer` / `arranger` / `description` | 否 | 乐器建议、作曲、编曲、描述等 |

完整格式与解析规则请参考官方 README 以及本仓库的 `AutoYuanQin/assets/tutorial_file/example.json`。

## 注意

- 曲谱文件请保持 UTF-8 编码且 JSON 合法。
- 本仓库只存放曲谱，不含 AutoYuanQin 脚本本体，脚本请从官方仓库获取。
