---
layout: post
title: PSG 使用指南
date: 2026-09-28 10:00:00+0800
description: PSG 实验操作图文指南，涵盖前期准备、电极安装、软件记录、数据导出与 EEGLAB 后续处理。
tags: [科研训练, PSG, 睡眠研究, 脑电, EEGLAB]
categories: [实验室指南]
---

作者：幸晓、姚梓枫

本指南介绍 PSG 实验的前期准备、设备与电极安装、软件监测和记录、数据导出，以及使用 EEGLAB 进行后续处理的操作流程。以下按原 PDF 页序展示完整图文，保留电极示意图、软件截图和操作标注。

[查看完整 PDF]({{ '/assets/pdf/psg-user-guide.pdf' | relative_url }}) · <a href="{{ '/assets/pdf/psg-user-guide.pdf' | relative_url }}" download>下载 PDF</a>

## 内容导航

- [第 1 页：前期准备](#page-01)
- [第 2 页：设备安装](#page-02)
- [第 3 页：电极安装](#page-03)
- [第 4 页：注意事项](#page-04)
- [第 5 页：配件参考图](#page-05)
- [第 6 页：软件与新建监测](#page-06)
- [第 7 页：信号检查与记录](#page-07)
- [第 8 页：数据提取](#page-08)
- [第 9 页：数据导出操作示例](#page-09)
- [第 10 页：后续处理和分析](#page-10)
- [第 11 页：滤波、重参考与保存](#page-11)
- [第 12 页：时间窗设置与特征统计](#page-12)

<h2 id="page-01">第 1 页：前期准备</h2>

<a href="{{ '/assets/img/posts/psg-user-guide/page-01.webp' | relative_url }}" target="_blank" rel="noopener">
  <img src="{{ '/assets/img/posts/psg-user-guide/page-01.webp' | relative_url }}" alt="PSG 使用指南第 1 页：前期准备" width="1061" height="1500" loading="lazy" style="display: block; width: 100%; height: auto;">
</a>

<h2 id="page-02">第 2 页：设备安装</h2>

<a href="{{ '/assets/img/posts/psg-user-guide/page-02.webp' | relative_url }}" target="_blank" rel="noopener">
  <img src="{{ '/assets/img/posts/psg-user-guide/page-02.webp' | relative_url }}" alt="PSG 使用指南第 2 页：设备安装" width="1061" height="1500" loading="lazy" style="display: block; width: 100%; height: auto;">
</a>

<h2 id="page-03">第 3 页：电极安装</h2>

<a href="{{ '/assets/img/posts/psg-user-guide/page-03.webp' | relative_url }}" target="_blank" rel="noopener">
  <img src="{{ '/assets/img/posts/psg-user-guide/page-03.webp' | relative_url }}" alt="PSG 使用指南第 3 页：电极安装" width="1061" height="1500" loading="lazy" style="display: block; width: 100%; height: auto;">
</a>

<h2 id="page-04">第 4 页：注意事项</h2>

<a href="{{ '/assets/img/posts/psg-user-guide/page-04.webp' | relative_url }}" target="_blank" rel="noopener">
  <img src="{{ '/assets/img/posts/psg-user-guide/page-04.webp' | relative_url }}" alt="PSG 使用指南第 4 页：注意事项" width="1061" height="1500" loading="lazy" style="display: block; width: 100%; height: auto;">
</a>

<h2 id="page-05">第 5 页：配件参考图</h2>

<a href="{{ '/assets/img/posts/psg-user-guide/page-05.webp' | relative_url }}" target="_blank" rel="noopener">
  <img src="{{ '/assets/img/posts/psg-user-guide/page-05.webp' | relative_url }}" alt="PSG 使用指南第 5 页：配件参考图" width="1061" height="1500" loading="lazy" style="display: block; width: 100%; height: auto;">
</a>

<h2 id="page-06">第 6 页：软件与新建监测</h2>

<a href="{{ '/assets/img/posts/psg-user-guide/page-06.webp' | relative_url }}" target="_blank" rel="noopener">
  <img src="{{ '/assets/img/posts/psg-user-guide/page-06.webp' | relative_url }}" alt="PSG 使用指南第 6 页：软件与新建监测" width="1061" height="1500" loading="lazy" style="display: block; width: 100%; height: auto;">
</a>

<h2 id="page-07">第 7 页：信号检查与记录</h2>

<a href="{{ '/assets/img/posts/psg-user-guide/page-07.webp' | relative_url }}" target="_blank" rel="noopener">
  <img src="{{ '/assets/img/posts/psg-user-guide/page-07.webp' | relative_url }}" alt="PSG 使用指南第 7 页：信号检查与记录" width="1061" height="1500" loading="lazy" style="display: block; width: 100%; height: auto;">
</a>

<h2 id="page-08">第 8 页：数据提取</h2>

<a href="{{ '/assets/img/posts/psg-user-guide/page-08.webp' | relative_url }}" target="_blank" rel="noopener">
  <img src="{{ '/assets/img/posts/psg-user-guide/page-08.webp' | relative_url }}" alt="PSG 使用指南第 8 页：数据提取" width="1061" height="1500" loading="lazy" style="display: block; width: 100%; height: auto;">
</a>

<h2 id="page-09">第 9 页：数据导出操作示例</h2>

<a href="{{ '/assets/img/posts/psg-user-guide/page-09.webp' | relative_url }}" target="_blank" rel="noopener">
  <img src="{{ '/assets/img/posts/psg-user-guide/page-09.webp' | relative_url }}" alt="PSG 使用指南第 9 页：数据导出操作示例" width="1061" height="1500" loading="lazy" style="display: block; width: 100%; height: auto;">
</a>

<h2 id="page-10">第 10 页：后续处理和分析</h2>

<a href="{{ '/assets/img/posts/psg-user-guide/page-10.webp' | relative_url }}" target="_blank" rel="noopener">
  <img src="{{ '/assets/img/posts/psg-user-guide/page-10.webp' | relative_url }}" alt="PSG 使用指南第 10 页：后续处理和分析" width="1061" height="1500" loading="lazy" style="display: block; width: 100%; height: auto;">
</a>

<h2 id="page-11">第 11 页：滤波、重参考与保存</h2>

<a href="{{ '/assets/img/posts/psg-user-guide/page-11.webp' | relative_url }}" target="_blank" rel="noopener">
  <img src="{{ '/assets/img/posts/psg-user-guide/page-11.webp' | relative_url }}" alt="PSG 使用指南第 11 页：滤波、重参考与保存" width="1061" height="1500" loading="lazy" style="display: block; width: 100%; height: auto;">
</a>

<h2 id="page-12">第 12 页：时间窗设置与特征统计</h2>

<a href="{{ '/assets/img/posts/psg-user-guide/page-12.webp' | relative_url }}" target="_blank" rel="noopener">
  <img src="{{ '/assets/img/posts/psg-user-guide/page-12.webp' | relative_url }}" alt="PSG 使用指南第 12 页：时间窗设置与特征统计" width="1061" height="1500" loading="lazy" style="display: block; width: 100%; height: auto;">
</a>
