# 更新日志 / Changelog

本文件记录贪吃蛇小游戏的版本变更。  
This file documents version changes of the Snake mini-game.

格式参考 / Format based on [Keep a Changelog](https://keepachangelog.com/zh-CN/1.1.0/).

---

## [1.1.0] — 2026-09-16

### 修复

#### 人机 / 双人
- 人机模式顶栏不再误显示单人数据，正确显示「你 / 电脑」得分与生命
- 双方不再共用同一移动节奏：减速、加速道具只影响持有者
- 双人 / 人机吃到磁铁后苹果可以正常吸附
- 开局时不再立刻取消道具动画循环，无敌闪烁、磁铁吸附表现更流畅
- 触控滑动在双人 / 人机模式下可控制 P1

#### 界面与交互
- 修复切换语言时访问不存在的 `langSublist` 导致报错、文案不刷新
- 规则 / 设置 / 确认等弹窗打开时，按空格不会误开始或重开
- 人机结算文案改为「你 · 电脑」（支持简体中文、繁體中文、English）

#### 玩法细节
- 复活时尽量避开障碍，减少落地立刻再死
- 磁铁不会把苹果吸进障碍格
- 单人绘制增加空蛇身保护，避免偶发崩溃

#### 清理
- 删除无效死代码与重复 CSS

### 新增

#### 状态栏
- 棋盘上方新增状态条
- 显示准备开始 / 进行中 / 已暂停 / 游戏结束
- 对局中显示双方道具倒计时，例如：`进行中 · 你 无敌 3s · 电脑 磁吸 5s`
- 道具结束后自动清理残留文案

#### 窗口设置（更多设置）
- 新增「窗口」选项
  - **原始**：普通窗口
  - **全屏**：进入浏览器全屏，棋盘随屏幕放大
- 偏好写入本地存储；按 Esc 退出全屏时同步为「原始」
- 说明：浏览器通常禁止无手势自动全屏，刷新后需再点一次「全屏」

#### AI 寻路
- 增加可达空间估算（洪水填充）
- 空间不足蛇身时重罚，减少自杀式钻缝
- 略偏好开阔区域、略偏向直行，减少无意义抖动

### 兼容性
- 单人基础玩法未改
- 兼容既有本地存档：最高分、语言、主题、音效、难度、初始生命
- 新增窗口模式偏好键 `snake-window-mode`

### 已知限制
- 刷新页面后无法自动恢复全屏，需手动再选一次
- AI 不是全局最优路径，只是明显更不容易自己堵死

---

### Fixed

#### VS CPU / 2 Players
- VS CPU HUD no longer shows solo data; it correctly shows You / CPU score and lives
- The two snakes no longer share one tick rate: slow and speed-up power-ups only affect the holder
- Magnet now pulls apples correctly in 2-player and VS CPU modes
- Power-up animation loop is no longer cancelled right at match start; blink and magnet effects are smoother
- Touch swipe controls P1 in 2-player and VS CPU modes

#### UI & Interaction
- Fixed a crash when switching language (reference to missing `langSublist`) that could leave stale text
- Space no longer starts or restarts the game while rules / settings / confirm dialogs are open
- VS CPU result text now uses “You · CPU” (Simplified Chinese, Traditional Chinese, English)

#### Gameplay
- Revive tries to avoid obstacles so you don’t die again immediately on landing
- Magnet no longer pulls apples into obstacle cells
- Solo draw is guarded against an empty snake body (avoids rare crashes)

#### Cleanup
- Removed dead code and duplicate CSS

### Added

#### Status bar
- New status strip above the board
- Shows Ready / Playing / Paused / Game Over
- During play, shows power-up countdowns for both sides, e.g. `Playing · You invincible 3s · CPU magnet 5s`
- Clears expired power-up text automatically

#### Window settings (More Settings)
- New **Window** option
  - **Original**: normal window
  - **Fullscreen**: browser fullscreen; board scales up
- Preference saved locally; exiting fullscreen with Esc syncs the setting to Original
- Note: browsers usually block fullscreen without a user gesture, so after reload you need to choose Fullscreen again

#### AI pathfinding
- Added reachable-space estimate (flood fill)
- Heavy penalty when free space is smaller than the snake body, reducing self-trapping
- Mild bias toward open areas and going straight to reduce twitchy moves

### Compatibility
- Solo core gameplay unchanged
- Existing local saves remain compatible: best score, language, theme, sound, difficulty, starting lives
- New window mode key: `snake-window-mode`

### Known limitations
- Fullscreen cannot auto-restore after a page reload; pick Fullscreen again manually
- AI is not globally optimal; it is mainly much less likely to box itself in

---

## [1.0.0]

### 功能
- 单人模式：方向键 / WASD，撞墙、撞自己扣命
- 双人对战：P1 WASD（绿），P2 方向键（橙）
- 人机对战：可选 WASD 或方向键，电脑为紫蛇
- 对战模式：积分赛 / 生存赛
- 难度：简单 / 默认 / 困难（困难含静止怪物与移动怪物）
- 道具：穿墙无敌、减速、磁铁、星星、红心加命
- 设置：语言（简 / 繁 / 英）、主题（浅 / 深 / 跟随系统）、音效、音乐、音量、初始生命
- 最高分本地保存
- 触控滑动支持

---

### Features
- Solo mode: arrow keys / WASD; hitting walls or yourself costs a life
- 2-player versus: P1 WASD (green), P2 arrows (orange)
- VS CPU: WASD or arrow keys; CPU is the purple snake
- Match types: Score Match / Survival
- Difficulty: Easy / Normal / Hard (Hard includes static and moving monsters)
- Power-ups: wall-pass invincibility, slow, magnet, star, heart (+1 life)
- Settings: language (ZH / ZH-Hant / EN), theme (light / dark / system), sound, music, volume, starting lives
- Best score saved locally
- Touch swipe support

---

## 版本说明 / Notes

- 文件 / File: `index..html`（单文件，无外部依赖 / single file, no external dependencies）
- 浏览器直接打开即可游玩 / Open directly in a browser to play
- 本地存档使用 `localStorage`，换浏览器或无痕模式不会同步  
  Saves use `localStorage` and do not sync across browsers or private mode
