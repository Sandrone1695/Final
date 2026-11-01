# 雨后森林音频场景设计
## 项目简介
本项目是基于 Wwise 制作的交互式游戏音频Demo，模拟热带雨林的听觉场景。
包含持续的2D环境基底音，以及多组3D随机音效，音效带有距离衰减效果，模拟声源远近变化。

## 使用工具与版本
- Wwise：2025.1.11
- Reaper：用于音频剪辑、混音与导出素材（48kHz / 24bit，WAV）

## 音频资产清单
1. Forest_Ambience_Base：2D环境背景音，循环播放，作为整个场景的底噪
2. RC_BirdCall：随机容器，包含3条鸟鸣采样，3D音效，带距离衰减
3. RC_InsectCall：随机容器，包含3条虫鸣采样，3D音效，带距离衰减

## 工程功能说明
1. 2D背景音：无衰减，全局持续播放，营造稳定的森林环境氛围
2. 随机容器（Random Container）：每次触发事件，随机播放容器内其中一条音频，避免音效重复单调
3. 距离衰减（Attenuation）：3D音效音量随声源与听者距离变化，模拟真实空间听觉
4. Event 事件系统：使用Play事件触发对应音频，供Soundcaster测试或者游戏引擎调用

## 测试方法
1. 使用 Wwise 打开 `Forest_Audio.wproj` 主工程文件
2. 顶部菜单 Views → Soundcaster（快捷键 Shift+S）打开Soundcaster测试会话
3. 将以下Event拖入Soundcaster面板：
   - Play_Ambience_Base
   - Play_BirdCall
   - Play_InsectCall
4. 保持右上角 LIVE 模式开启
   - 点击 Play_Ambience_Base 播放背景循环音
   - 点击其余事件，触发随机音效；拖动 Emitter 和 Listener 滑块，测试距离衰减效果