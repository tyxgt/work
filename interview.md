<font style="color:rgba(0, 0, 0, 0.9);">情指行：情报、指挥、行动</font>

# <font style="color:rgba(0, 0, 0, 0.9);">项目简介</font>
<font style="color:rgba(0, 0, 0, 0.9);">指调与应急产品线：指挥调度与应急通信产品线</font>

<font style="color:rgba(0, 0, 0, 0.9);">所在部门为  指调与应急产品线/指调开发部/指调软件一组</font>

<font style="color:rgba(0, 0, 0, 0.9);">主要参与的是AIA警情分析系统（Alarm-intelligence-analysis），也可以叫做情指知识库。</font>

<font style="color:rgba(0, 0, 0, 0.9);">情指知识库： 属于是整个指调系统数据流转的下游系统，因为AIA系统主要进行分析与统计的数据都是来自于ICC或VCS。例如接警单数据、话务数据、坐席数据来自于ICC，处警数据、反馈数据、当事人数据、证据单、警情处理信息等来自于VCS。AIA系统通过ETL工具将这些数据从上游的数据库中抽取到AIA自身的数据库中，然后通过将数据转存到ElasticSearch，利用ElasticSearch强大的数据检索和聚合能力将数据进行多种维度的统计，最终通过浏览器页面提供给用户查看  </font>

# 警情画像
重点在列表组件

# 水印
> 问题就是禁用js的话，水印会被删除掉
>

```javascript
/*
 * @Author: master
 * @Date: 2021-12-06 15:50:36
 * @LastEditTime: 2023-10-07 16:14:32
 * @Description: 水印
 */
import { getUuid } from './units.js';
import _ from 'lodash';
const constant = {
  container: document.body, // canvas渲染位置
  width: 500, // 每块img宽度
  height: 400, // 每块img高度
  font: 'normal 16px 思源黑体_ Regular', // 文字字体
  fillStyle: 'rgba(8, 90, 125, 0.1)', // 文字颜色
  content: '水印', // 文字内容，换行用\n
  rotate: 20, // 文字层翻转角度
  zIndex: 99999, // 元素层叠等级
  left: 0, // 元素居左距离
  top: 0, // 元素居上距离
  offsetLeft: 240, // 偏移居左
  offsetTop: 200, // 偏移居右
  fontOffsetLeft: 100, // 文字偏移居左
  fontOffsetTop: 150, // 文字偏移居右
};
// 创建水印base64图片
const createImgBase = (options) => {
  const canvas = document.createElement('canvas');
  canvas.setAttribute('width', options.width);
  canvas.setAttribute('height', options.height);
  const ctx = canvas.getContext('2d');

  ctx.font = options.font;
  ctx.fillStyle = options.fillStyle;
  // ctx.textAlign = 'center';
  ctx.rotate((Math.PI / -180) * options.rotate);
  // 分割水印内容
  const arrayContent = options.content ? options.content.split('\n') : '水印';
  options.x = options.x | 0;
  options.y = options.y | 0;
  arrayContent.forEach((item, index) => {
    const cIdex = index === 0 ? 1 : index + 1;
    ctx.fillText(item, 0, cIdex * 30 + options.y + options.fontOffsetTop);
  });
  const base64Url = canvas.toDataURL();
  return base64Url;
};
/**
 * canvas 实现 watermark
 * @param {Object} param
 */
const CanvasWM = (option = {}) => {
  let options = {
    ...constant,
    ...option,
  };
  // 定时器
  let intervalOut;
  const uuid = option.uuid || getUuid();
  const [watermarkDiv, watermarkDivDis] = [
    document.createElement('div'),
    document.createElement('div'),
  ];
  try {
    const base64Url = createImgBase({ ...options });
    const base64UrlDis = createImgBase({ ...options });
    const styleStr = `
      position:absolute;
      top:${options.top}px;
      left:${options.left}px;
      bottom:0;
      right:0;
      z-index:${options.zIndex};
      pointer-events:none;
      background-image:url('${base64Url}')`;
    const styleStrDis = `
      position:absolute;
      top:${options.offsetTop}px;
      left:${options.offsetLeft}px;
      bottom:0;
      right:0;
      z-index:${options.zIndex};
      pointer-events:none;
      background-image:url('${base64UrlDis}')`;
    const [divUuid, divDisUuid] = [uuid, `${uuid}-dis`];
    watermarkDiv.setAttribute('style', styleStr);
    watermarkDivDis.setAttribute('style', styleStrDis);
    watermarkDiv.setAttribute('id', divUuid);
    watermarkDivDis.setAttribute('id', divDisUuid);
    /**
     * 渲染水印
     */
    const renderWM = () => {
      if (options.container) {
        options.container.style.position = 'relative';
        options.container.appendChild(watermarkDiv);
        options.container.appendChild(watermarkDivDis);
      }
    };
    // 渲染水印
    renderWM();
    // 清除水印
    const remove = () => {
      const watermark = document.getElementById(divUuid);
      const watermarkDis = document.getElementById(`${uuid}-dis`);
      if (watermark) options.container.removeChild(watermark);
      if (watermarkDis) options.container.removeChild(watermarkDis);
    };
    // 此方法是防止用户通过 开发者工具 修改样式/或直接删除 祛除水印
    const observer = new MutationObserver(() => {
      const watermark = document.getElementById(divUuid);
      const watermarkDis = document.getElementById(`${uuid}-dis`);
      if (!watermark || !watermarkDis) {
        // 清除水印
        remove();
        // 渲染水印
        renderWM();
      }
    });
    observer.observe(document.body, {
      childList: true, // 观察目标子节点的变化，是否有添加或者删除
      attributes: true, // 观察属性变动
      subtree: true, // 观察后代节点，默认为 false
    });
    // 开启定时任务
    if (
      options?.loopDuration &&
      _.isNumber(options.loopDuration) &&
      options?.loopCallBack &&
      _.isFunction(options.loopCallBack)
    ) {
      // 最少10秒钟
      if (options.loopDuration <= 10000) {
        options.loopDuration = 10000;
      }
      // 设置Interval定时器
      intervalOut = setInterval(() => {
        // 重新获取渲染参数
        const option = options.loopCallBack();
        if (_.isPlainObject(option)) {
          // 重新设置渲染参数
          options = { ...options, ...option };
          // 清除水印
          remove();
          // 渲染水印
          renderWM();
        } else {
          clearInterval(intervalOut);
        }
      }, options.loopDuration);
    }
    return {
      uuid,
      remove,
    };
  } catch (e) {
    console.error(e);
    if (intervalOut) clearInterval(intervalOut);
  }
};
// 调用
export default CanvasWM;

// units.js
export const getUuid = () => {
  const S4 = () => {
    return (((1 + Math.random()) * 0x10000) | 0).toString(16).substring(1);
  };
  return (
    S4() +
    S4() +
    '-' +
    S4() +
    '-' +
    S4() +
    '-' +
    S4() +
    '-' +
    S4() +
    S4() +
    S4()
  );
};
```

<font style="color:rgba(0, 0, 0, 0.9);"></font>

