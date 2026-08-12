# Codex Dream Skin Dynamic WebP

<p align="center">
  <strong>给 Codex Dream Skin 加上一张真正会动的背景。</strong><br>
  Animated WebP · 动态背景 · 循环动画
</p>

<p align="center">
  固定画面 · 局部动态 · 连续变化
</p>

<p align="center">
  <img src="background.webp" alt="Codex Dream Skin Animated WebP" width="900">
</p>

<p align="center">
  <sub>Animated WebP 动态背景示例</sub>
</p>

---

## WebP 为什么能做动态

WebP 不只是静态图片格式，也支持 **Animated WebP**。

Animated WebP 可以在一个 `.webp` 文件中保存多帧画面，并记录每一帧的显示时间和循环方式。

播放时会按照顺序不断切换：

```text
Frame 01 → Frame 02 → Frame 03 → ... → Frame 01
```

因此 Dream Skin 实际加载的仍然只是一张：

```text
background.webp
```

但这个文件内部包含多帧画面，所以最终看到的是持续循环的动态背景。

---

## 制作原理

动态 WebP 制作的核心是：

> **以同一张原图为基础，固定整体画面，只让需要运动的部分产生连续变化。**

```text
静态原图
    ↓
锁定整体画面
    ↓
局部产生连续变化
    ↓
生成连续帧
    ↓
保证首尾自然循环
    ↓
Animated WebP
```

不要让 AI 每一帧重新生成整个场景，否则容易产生闪烁、变形和位置漂移。

---

## 如何制作

制作时主要注意：

* **固定原图**：整体构图保持不变
* **局部动态**：只改变真正需要运动的区域
* **帧间一致**：连续帧中的主体和结构保持稳定
* **首尾循环**：最后一帧能够自然连接第一帧

对于桌面环境动态，一般使用约：

```text
24 ～ 32 帧
3 ～ 5 秒循环
```

即可获得比较自然的效果。

> **不是让整张图片动起来，而是在同一张图片上制造连续变化。**

---

## 参考文件

本仓库包含完整示例：

* [`background.webp`](./background.webp) — Animated WebP 动态背景
* [`theme.json`](./theme.json) — Dream Skin 主题配置
* [`theme.css`](./theme.css) — UI 透明度与界面样式
* [`ink-rain.zip`](./ink-rain.zip) — 完整主题 ZIP

---

### theme.json

用于指定动态背景、主题颜色、焦点位置和安全区域。

<details>
<summary><strong>查看 theme.json</strong></summary>

```json
{
  "schemaVersion": 1,

  "id": "ink-rain",

  "name": "闲来垂钓碧溪上",

  "brandSubtitle": "忽复乘舟梦日边",

  "tagline": "·",

  "projectPrefix": "· ",

  "projectLabel": "·",

  "statusText": "·",

  "quote": "闲来垂钓碧溪上",

  "image": "background.webp",

  "appearance": "light",

  "art": {
    "focusX": 0.72,
    "focusY": 0.50,
    "safeArea": "left",
    "taskMode": "ambient"
  },

  "colors": {
    "background": "#E9E7E1",

    "panel": "rgba(232, 233, 228, 0.68)",

    "panelAlt": "rgba(218, 222, 218, 0.54)",

    "accent": "#748C8A",

    "accentAlt": "#A9B9B5",

    "secondary": "#6F7470",

    "highlight": "rgba(238, 241, 236, 0.76)",

    "text": "#2D302E",

    "muted": "#747A76",

    "line": "rgba(73, 82, 78, 0.15)"
  }
}
```

</details>

---

### theme.css

用于调整 Codex UI 的透明度，让动态背景能够透过界面显示。

<details>
<summary><strong>查看 theme.css</strong></summary>

```css
[data-ds-part="root"] {
  background-color: var(--ds-theme-color-background);
  color: var(--ds-theme-color-text);
  border-color: var(--ds-theme-color-line);
}


[data-ds-part="sidebar"] {
  background-color: rgba(247,243,235,0.40);
  border-color: rgba(91,82,73,0.08);
  border-width: 1px;
  border-style: solid;
  border-radius: 18px;
  box-shadow: 0 5px 18px rgba(48,42,36,0.04);
}


[data-ds-part="sidebar"]:hover {
  background-color: rgba(250,247,240,0.48);
  border-color: rgba(91,82,73,0.11);
}


[data-ds-part="main"] {
  background-color: transparent;
  border-color: rgba(91,82,73,0.08);
  border-width: 1px;
  border-style: solid;
  border-radius: 20px;
}


[data-ds-part="header"] {
  background-color: rgba(248,245,238,0.12);
  border-color: rgba(91,82,73,0.08);
  border-width: 1px;
  border-style: solid;
  border-radius: 16px;
}


[data-ds-part="home"] {
  background-color: transparent;
}


[data-ds-part="home-hero"] {
  background-color: rgba(248,245,238,0.20);
  border-color: rgba(91,82,73,0.10);
  border-width: 1px;
  border-style: solid;
  border-radius: 22px;
  box-shadow: 0 5px 20px rgba(48,42,36,0.04);
}


[data-ds-part="project-list"] {
  background-color: rgba(250,247,240,0.22);
  border-color: rgba(91,82,73,0.09);
  border-width: 1px;
  border-style: solid;
  border-radius: 16px;
}


[data-ds-part="thread"] {
  background-color: rgba(247,244,237,0.10);
  border-color: rgba(91,82,73,0.06);
  border-width: 1px;
  border-style: solid;
  border-radius: 18px;
}


[data-ds-part="message"] {
  background-color: rgba(250,247,240,0.24);
  border-color: rgba(91,82,73,0.09);
  border-width: 1px;
  border-style: solid;
  border-radius: 16px;
  box-shadow: 0 4px 14px rgba(48,42,36,0.035);
}


[data-ds-part="composer-toolbar"] {
  background-color: rgba(252,249,243,0.38);
  border-color: rgba(91,82,73,0.11);
  border-width: 1px;
  border-style: solid;
  border-radius: 14px;
}


[data-ds-part="dialog"] {
  background-color: rgba(248,245,238,0.84);
  border-color: rgba(91,82,73,0.18);
  border-width: 1px;
  border-style: solid;
  border-radius: 20px;
  box-shadow: 0 12px 32px rgba(48,42,36,0.14);
}
```

</details>

---

## Related Project

<p align="center">
  <a href="https://github.com/Fei-Away/Codex-Dream-Skin">
    <strong>Codex Dream Skin</strong>
  </a>
</p>

<p align="center">
  <sub>本项目仅分享 Animated WebP 动态背景制作与主题参考。</sub>
</p>

---

## 声明

非 OpenAI 官方项目。

Codex Dream Skin 为第三方项目，相关权利归其各自权利人。

---

如果这个方法对你有帮助，可以点一个 ⭐ Star。
