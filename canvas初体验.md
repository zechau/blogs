# canvas 初体验
## 引入canvas

1. 在页面中适当位置加入Canvas标签
```html
<canvas id="canvas"></canvas>
```
2. 初始化画布工具
```javascript
    // 获取画布Dom
    const canvas = document.getElementById('canvas');

    // 获取绘图环境
    const context = canvas.getContext('2d');

    //设置画布宽高，适配屏幕分辨率，解决canvas在高清屏上显示模糊问题
    const ratio = window.devicePixelRatio || 1;
    canvas.width = 200 * ratio;
    canvas.height = 100 * ratio; 
    canvas.getContext('2d').setTransform(ratio, 0, 0, ratio, 0, 0);

    // 开始绘制
    context.save();
    context.fillStyle = "blue";
    context.arc(80, 60, 20, 0, 2 * Math.PI);
    context.stroke();
    context.fill();
    context.restore();

```
    
## 注意事项
1. canvas有自己的坐标系，画布上的元素是基于画布左上角进行定位，屏幕坐标不能直接用于绘制定位，需要转换成相对于canvas的坐标
2. 绘制时建议先调用save方法，保存当前环境设置，比如填充颜色，原点偏移避免不通图形的绘制设置冲突污染（一开始可以不这么做，踩踩坑体验下），
绘制完成后，调用restore恢复上次保存的环境设置。