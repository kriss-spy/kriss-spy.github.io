```python
import selfstudy

def my_college_life(study):
    study = replace_with_selfstudy(study)
    study = study.optimize()

my_college_life(HUST AIA Automation)
```
<!--
<div style=" width: 100%; height:220;overflow: hidden; "><iframe src="https://widget.pkmer.cn/free/BongoCat?user=3285d6c1-2db8-4a90-8173-d38255e5b447&theme=%E4%BA%AE%E8%89%B2%E6%A8%A1%E5%BC%8F&select-theme=light" allow="fullscreen" style=" height: 100%; width: 100%;"></iframe></div>
-->

<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>动态图显示</title>
<style>
  :root {
    --iframe-background: #ffffff; /* 浅色模式背景颜色 */
    --iframe-background-dark: #121212; /* 深色模式背景颜色 */
  }

  .iframe-container {
    width: 100%;
    height: 220px;
    overflow: hidden;
    background-color: var(--iframe-background); /* 默认背景颜色 */
  }

  /* 深色模式媒体查询 */
  @media (prefers-color-scheme: dark) {
    .iframe-container {
      background-color: var(--iframe-background-dark);
    }
  }

  iframe {
    height: 100%;
    width: 100%;
    border: none;
  }
</style>
</head>
<body>

{% if site.dark_mode %}
<div class="iframe-container">
  <iframe src="https://widget.pkmer.cn/free/BongoCat?user=3285d6c1-2db8-4a90-8173-d38255e5b447&theme=%E6%9A%97%E8%89%B2%E6%A8%A1%E5%BC%8F&select-theme=dark" allow="fullscreen"></iframe>
</div>
{% else %}
<div class="iframe-container">
  <iframe src="https://widget.pkmer.cn/free/BongoCat?user=3285d6c1-2db8-4a90-8173-d38255e5b447&theme=%E4%BA%AE%E8%89%B2%E6%A8%A1%E5%BC%8F&select-theme=light" allow="fullscreen"></iframe>
</div>
{% endif %}

</body>
</html>


[contact me](about.md)

[for fun](test.md)

[see my latest study](https://blog.csdn.net/2301_81944256?spm=1011.2415.3001.5343)

updated 6/13
