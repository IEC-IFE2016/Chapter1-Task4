# Chapter1-Task4-Vizards
> 百度IFE - 第一阶段 - 任务4 - 定位和居中问题

### 任务描述
- 实现如下图的效果
  ![定位和居中问题效果图](http://7xrp04.com1.z0.glb.clouddn.com/task_1_4_1.png)
- 灰色元素水平垂直居中，有两个四分之一圆位于其左上角和右下角
- 调节浏览器宽度，灰色元素始终水平居中
- 调节浏览器高度，灰色元素始终垂直居中
- 调节浏览器高度和宽度，黄色扇形的定位始终准确

### 参考资料
- [HTML和CSS高级指南之二——定位详解](http://www.w3cplus.com/css/advanced-html-css-lesson2-detailed-css-positioning.html)：大漠老师手把手教你，这次彻底搞懂定位问题
- [Centering in CSS: A Complete Guide](https://css-tricks.com/centering-css-complete-guide/)：完整讨论了不同情况下的居中方案，建议自己思考之后再看答案
- [Get HTML & CSS Tips In Your Inbox](http://howtocenterincss.com/)：有人写了一个作弊工具生成居中代码，但是看着代码你明白为什么吗

### 实现总结
1. 当需要被居中的div的宽高已知时，我们可以使用绝对定位配合left、top的定位来完成居中
  ```
  div {
    width: @width;
    height: @height;
    position: absolute;
    left: 50%;
    top: 50%;
    /*
     * 当设置完left和top之后,我们会发现图片到了正中央的偏右下方
     * 这是因为50%指的是浏览器当前高度和宽度的50%,这样就会刚好多出来一个container的高度和宽度
     * 所以解决方法就是设置负margin,hack掉多出来的高度和宽度
     */
    margin-left: -(@width / 2);
    margin-top: -(@height / 2);
  }
  ```
  
2. 当需要被居中的div宽高未知时，我们需要：
  - 将被居中的div的父级元素设为```position: relative```
  - 对被居中的div设置CSS3 transform
  - 示例代码：
  
    ```
    .parent {
      position: relative;
    }
    .child {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
    ```
  
3. 使用top、right、bottom、left时，注意它们都是以自身div的左上角为定位点，相对父级元素的定位。
   使用负值即可让子div超出父div
   
### 任务完成情况
- [x] 代码实现
- [x] 任务总结
- [x] 任务提交   
