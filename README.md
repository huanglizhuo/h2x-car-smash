# H2-X 砸车关

一个 90 年代街机格斗风的砸车奖励关。主角是宇树 H2-X 人形机器人，在参考《Super Street Fighter II》Bonus Stage 的白天海港中限时砸车。

**在线试玩：** https://h2x-car-smash.pages.dev/

**GitHub Pages：** https://huanglizhuo.github.io/h2x-car-smash/

## 操作

| 键盘 | 动作 |
|---|---|
| Enter | 开始 / 重来 |
| A D（或 ← →） | 移动 |
| W（或 ↑） | 跳 |
| S（或 ↓） | 蹲 |
| U I O | 轻 / 中 / 重拳 |
| J K L | 轻 / 中 / 重脚 |
| → + 拳 | 下压肘击 |
| → + 脚 | 膝撞 |
| 空中 ↓ + 拳 / 脚 | 坠肘 / 踩踏 |
| ↓↘→ + 拳 | 崩拳 |
| ↓↙← + 脚 | 旋风腿 |
| →↓↘ + 脚 | 铁花空翻 |
| M | 静音 |

手机上碰一下屏幕，就会出现虚拟摇杆和按键；三个必杀技有一键快捷键。

汽车使用指定的 SSFII 原版精灵表，画面宽度为 228 像素（原来约 184 像素）。车分车头、车厢、车尾三段，各有三级损坏。可以从两侧跳上车顶；在车顶按拳会下砸，按脚会踩踏。40 秒内全部砸烂就是 PERFECT，随后结算剩余时间奖励。

## 技术

游戏代码在 `index.html`，素材在 `assets/`，没有依赖或构建步骤。保留目录结构后可以直接用浏览器打开，也可以运行 `python3 -m http.server 8088` 后访问 `http://localhost:8088`。

- H2-X 角色由 SDF 形状、调色板量化和自动描边生成；海港场景由 Canvas 绘制。
- 汽车、车架和碎片使用本地精灵表，分区切换破损帧；加载失败时显示错误提示。
- 音效用 WebAudio 实时合成。
- 打开 `index.html#test` 或 `http://localhost:8088/#test` 会运行自检：两侧攻击、单次命中、车顶落脚与下砸、64 种破损组合、胜负和重开。

## 发布

Cloudflare Pages 项目名：`h2x-car-smash`，生产分支：`main`。当前采用 Wrangler Direct Upload，Git push 不会自动触发 Cloudflare 部署。将 `index.html` 和 `assets/` 复制到一个干净的发布目录后运行：

```sh
npx wrangler pages deploy <发布目录> --project-name h2x-car-smash --branch main
```

## 声明

粉丝作品，与宇树科技（Unitree）和 Capcom 均无关联。H2-X 是宇树科技的产品名。汽车及相关特效使用 Capcom 的原游戏素材，来源和署名见 [assets/README.md](assets/README.md)。场景是参考原作的代码重绘，H2-X 动作与音效仍由本项目实现，未声称是原版逐帧复刻。
