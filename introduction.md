# 离职原因
<font style="color:rgb(102, 102, 102);background-color:rgb(248, 248, 248);">在</font><font style="color:rgb(102, 102, 102);">原公司所负责的工作内容比较单一且重复性比较高，无法满足我个人的职业发展需求。我想找一个更有挑战性、并且更有成长空间的工作。</font>

# 自我介绍
> 姓名，年龄，毕业学校，实习，现在在哪工作
>

面试官你好，我叫田昀鑫，今年22岁，2023年（也就是今年）毕业于西安邮电大学信息对抗技术专业，之前有过一段半年的在字节的实习经历，目前就职于海能达通信股份有限公司。实习期间主要参与的是Pico社区论坛，Pico开发者论坛以及社区中台组件库的开发，用的是React，然后目前工作是负责警情分析系统的开发工作，系统主要使用的版本是vue2。接下来我简单介绍一下我参与的这几个项目。

Hello interviewer,

My name is Tian Yunxin, and I'm 22 years old. I graduated from Xi'an University of Posts and Telecommunications in 2023 with a major in Information Countermeasures Technology. Prior to that, I had a six-month internship experience at Byte, and currently, I am employed at Hainengda Communication Co., Ltd.

During my internship, I primarily worked on the development of the Pico Community Forum, Pico Developer Forum, and the Community Middleware Component Library, using React. Currently, my role involves developing the Alert Analysis System, which primarily utilizes Vue2.

I am passionate about front-end development and have hands-on experience with popular frameworks and libraries. I am eager to contribute my skills and knowledge to the team and learn from experienced professionals. Thank you for considering my application, and I look forward to discussing how I can contribute to your organization.

# Pico
> pico成立于2015年3月，是全球知名的具备独立创新和研发出按照能力的VR/AR品牌，2021年9月被字节收购
>
> webxr前身是webvr，现在是webvr(虚拟现实)+webar（增强现实），webxr是一组支持将渲染3D场景用来呈现虚拟世界（虚拟现实，也称作VR）或将图形图像添加到现实世界的标准。webxr设备api实现了webxr功能集的核心，管理输出设备的选择，以适当的帧速率将3D场景呈现给所选设备，并管理使用输入控制器创建的运动矢量
>

## Pico社区论坛
是Picovr用户乃至其他vr用户分享交流的平台，包括pc端，h5以及app的内嵌页

### jupiter
> [迈入现代 Web 开发（GMTC 2021 演讲《字节跳动的现代 Web 开发实践》全文）](https://zhuanlan.zhihu.com/p/386607009)
>

基于react的渐进式现代Web开发框架，从三种工程方案出发（应用工程方案，模块工程方案，monorepo工程方案），支持全链路的前端研发。

    - 应用工程方案：
        * Cli，servert，runtime
    - 模块工程方案：
        * 用于开发可复用模块，主要提供编译构建的能力，插件方面则是主要提供了调整编译构建配置的 Hook。
    - monorepo工程方案
+ 应用初始化可以对项目进行简单的配置，比如开发语言，包管理工具等。在初始化的过程中也不会内置所有官网的功能，如果内置功能不满足需要也可以使用官方插件来扩展功能。在创建项目之后我们可以通过命令行字懂的开启jupiter官方支持的功能，比如国际化i18n，less/sass支持等
+ 我们也可以在jupiter初始化模板项目的基础上通过生成器插件对模板进行增加，删除，修改的方法
+ [unbundle模式](https://juejin.cn/post/7143136313720766471)极速开发，会极大提升服务启动的速度。有使用 Webpack 启动需要 200s 左右的项目，使用 Unbundled 后只花费 10s，开发调试提速 20 倍。
+ 服务端渲染：在jupiter.config.js文件中配置server:{ssr: true}}即可

### hybrid（混合开发）
pico vr助手是一个hybrid app，将app的一部分需要的动态变化的内容通过h5来实现，通过原生的网页加载控件webview（安卓）或WKWebview（ios）来加载h5页面，这样做的好处是h5页面可以随时改变不用发版，动态化满足需求，同时H5的页面只需要一次开发就可以在android和ios两个平台运行。

优点：可以跨平台，调试方便，维护成本低，不用发版解决问题

缺点：需要多端配合，不适用交互性强的app

### webview
1. <font style="color:rgb(18, 18, 18);">Webview 是一个基于webkit的引擎，可以解析DOM 元素，展示html页面的控件，它和浏览器展示页面的原理是相同的，所以可以把它当做浏览器看待。</font>
2. 在做移动端h5开发时，需要与native之间进行交互，而在native中，h5的承载容器为webview，核心是使用webview控件实现加载url。  webview就是用来展示网页的view组件。WebView 是手机中内置了一款高性能 Webkit 内核浏览器，在 SDK 中封装的一个组件。不过没有提供地址栏和导航栏，只是单纯的展示一个网页界面。**可以理解为是页面里面的iframe**。
3. 渲染流程：**<font style="color:#DF2A3F;background-color:#C1E77E;">（需要查询，todo）</font>**

在安卓渲染过程中，ui线程进行绘制的时候，如果有web内容，会调用到webkit thread线程来遍历web中的doc文件，然后生成一个display list，交给ui线程中的display list进行渲染

### jsbridge
> [深入浅出JSBridge：从原理到使用 - 掘金](https://juejin.cn/post/6936814903021797389)
>

**Pico大多数是js api，也就是向web中注入js，schema**

以js引擎或webview容器作为媒介，通过协定协议进行通信，实现Native端和web端双向通信的一种机制。

>  给js提供调用native功能的接口，是native与非native之间的桥梁。核心是构建native与非native间消息通信的通道，是双向通信的
>

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697036208082-c87495d1-58f3-4207-873e-10a6da95227b.png)

**native => web**

将拼接的js代码字符串，传入js解析器（webview）执行

> 仅需要h5将js方法暴露在window上给Native调用即可![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697038526105-33d94fea-74a1-413d-94c7-02623d58b4df.png)
>

**web => native**

1. **拦截webview请求的url schema**

> url schema<font style="color:rgb(113, 119, 125);">是App提供给外部的可以直接操作App的规则</font>
>
> <font style="color:rgb(113, 119, 125);">客户端和前端定义Scheme规范，前端加载scheme，客户端进行拦截，判断请求类型后进行执行对应逻辑</font>![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697038603638-149f97c2-ba81-4604-ba2f-b6e12bcbf781.png)
>

<font style="color:rgb(113, 119, 125);">Native加载WebView之后，Web发送的所有请求都会经过WebView组件，所以Native可以重写WebView里的方法，从来拦截Web发起的请求，我们对请求的格式进行判断：</font>

    - 如果符合我们自定义的URL Schema，对URL进行解析，拿到相关操作、操作，进而调用原生Native的方法
    - 如果不符合我们自定义的URL Schema，我们直接转发，请求真正的服务

web发送url请求的方法的方式

    - a标签
    - location.href
    - 使用iframe.src
    - 发送ajax请求
2. **向webview中注入js api**

这个方法会通过webView提供的接口，App将Native的相关接口注入到JS的Context（window）的对象中，一般来说这个对象内的方法名与Native相关方法名是相同的，Web端就可以直接在全局window下使用这个暴露的全局JS对象，进而调用原生端的方法。**此方法通信时间短，调用方便**

**jsb的权限校验**

由于第三方应用的存在，为了保证端能力调用的安全性，防止恶意软件或者网页随意获取用户信息，则需要对第三方调用jsb的能力进行管理

权限分类：

+ Private ： 只有内网才可以访问
+ protected： 第三方域名调用时需要进行权限校验
+ Public: 所有域名的都可以进行访问

**管理流程：**

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697038680628-555af303-9feb-4c48-92f6-188b363213d2.png)

### 埋点
埋点是用来进行数据采集的，针对特定用户行为或时间进行捕获，处理以及发送的相关技术及其实施过程。埋点是数据的来源，采集的数据可以分析网站/APP的使用情况，用户行为习惯等，是建立用户画像，用户行为路径等数据产品的基础。（目前pico使用的是代码埋点的方式）

**手机助手中的埋点需要与客户端同学配合进行工作，所以是hybrid页面中的埋点由客户端进行上报，前端只是调用了jsb将参数传递过去**

**common组件中customEventNode.ts中会创建CustomEventNode，该类中通过事件总线的方式添加事件监听，取消事件监听，抛出事件。DataEventProvider中创建一个CustomEventNode实例，然后传入React.createContext，然后在之后需要进行埋点的地方使用DataEventProvider就可以使用**

**在DataEvent中，会使用到DataEventContext，并在useEffect中注册我们需要监听的事件**

```javascript
hybrid/hooks/useAppTrackHook.ts
/** 事件处理中心 */
function useAppTrackHook() {
  const eventDataRef = useRef<any>(null);
  useEffect(() => {
    const picoEvent = eventDataRef.current;
    if (!picoEvent) {
      return undefined;
    }
    // click_report埋点
    const clickReport = picoEvent.on('click_report', ({ data }) => {...});
    return () => {
      clickReport();
    };
  }, [eventDataRef.current]);
  return [eventDataRef];
}
export default useAppTrackHook;
_app.tsx——页面根组件
import useAppTrackHook from '../hooks/useAppTrackHook';
const App = ({ Component, ...pageProps }: { Component: React.ComponentType }) => {
const [eventDataRef] = useAppTrackHook();
  return (
  // 当我们需要传递参数时也可以在tsx中包裹<DataEventProvider></DataEventProvider>
    <DataEventProvider ref={eventDataRef} evtData={{ root: 'hybrid', appid: '264482' }}>
      <div id="app">
        <Component {...pageProps} />
      </div>
    </DataEventProvider>
  )
}
hybrid/pages
export default ()=>{
  const dataEventContext = useContext(DataEventContext);    
  const onUserClick = user => {
    dataEventContext.trigger('click_user', {
      user,
    });
  };
}
DataEventProvider/index.tsx
import React, { forwardRef, PropsWithChildren, useContext, useEffect, useImperativeHandle, useMemo } from 'react';
import CustomEventNode from './CustomEventNode';
interface DataEventProps {
  evtData: any;
  /** block 状态, 为 true 时暂存当前事件,待 block 状态解除再发送 */
  block?: boolean;
}
const rootEventNode = new CustomEventNode();
/** 社区中台组件全局配置Context */
export const DataEventContext = React.createContext<CustomEventNode>(rootEventNode);
/** 社区中台事件中心节点 */
const DataEventProvider = forwardRef<CustomEventNode, PropsWithChildren<DataEventProps>>(({ evtData, block, children }, ref) => {
  const evtObj = useMemo(() => new CustomEventNode(), []);
  const parentEvtObj = useContext(DataEventContext);
  useEffect(() => {
    evtObj.setParent(parentEvtObj);
  }, [parentEvtObj, evtObj]);
  useEffect(() => {
    evtObj.block = Boolean(block);
  }, [block, evtObj]);
  useEffect(() => {
    evtObj.evtData = evtData;
  }, [evtData, evtObj]);
  useImperativeHandle(ref, () => evtObj, [evtObj]);
  return <DataEventContext.Provider value={evtObj}>{children}</DataEventContext.Provider>;
});
export default DataEventProvider;
DataEventProvider/CustomEventNode.ts
import { cloneDeep } from 'lodash';
const EventListenSymbol = Symbol('EventListen');
const EventCatchSymbol = Symbol('EventCatch');
const InnerProp = Symbol('InnerProp');
interface EventData {
  name: string;
  data: any;
  context: any[];
}
interface EventListenRecord {
  handle: (data: EventData) => void;
  once: boolean;
}
let i = 1;
interface EventCatchItem {
  evtName: string;
  evtData: any;
}
class CustomEventNode {
  /** 事件监听池 */
  [EventListenSymbol]: { [key: string]: Set<EventListenRecord> };
  /** 缓存事件池 */
  [EventCatchSymbol]: Set<EventCatchItem>;
  /** 内部状态 */
  [InnerProp]: {
    id: number;
    /** block 状态, block 状态下 trigger 的事件会被暂存, 带状态解除再发出 */
    isBlock: boolean;
    parent: null | CustomEventNode;
    eventData: any;
  };
  constructor() {
    this[InnerProp] = Object.create(null);
    this[EventListenSymbol] = Object.create(null);
    this[EventCatchSymbol] = new Set();
    this[InnerProp].id = i++;
    this[InnerProp].isBlock = false;
    this[InnerProp].parent = null;
    this[InnerProp].eventData = {};

    if (process.env.NODE_ENV === 'development') {
      window.CommunityEventNodes = window.CommunityEventNodes || [];
      window.CommunityEventNodes.push(this);
    }
  }
  get id() {
    return this[InnerProp].id;
  }
  get evtData() {
    return this[InnerProp].eventData;
  }
  set evtData(val) {
    this[InnerProp].eventData = val;
  }
  get block() {
    return this[InnerProp].isBlock;
  }
  set block(status: boolean) {
    const oldStatus = this[InnerProp].isBlock;
    this[InnerProp].isBlock = status;
    // 解禁
    if (!status && oldStatus) {
      // 把缓存事件都发出并情况事件缓存池(注意死循环), 同步代码应该没问题
      this[EventCatchSymbol].forEach(eventItem => {
        this.trigger(eventItem.evtName, eventItem.evtData);
      });
      this[EventCatchSymbol].clear();
    }
  }
  setParent(parent: CustomEventNode) {
    this[InnerProp].parent = parent;
  }
  getContext(): any[] {
    const ctx = this[InnerProp].parent?.getContext() || [];
    ctx.unshift(this[InnerProp].eventData);
    return ctx;
  }
  /** 添加事件监听, 仅监听一次 */
  once(evtName: string, fuc: (evt: EventData) => void): () => void {
    this[EventListenSymbol][evtName] = this[EventListenSymbol][evtName] || new Set();
    this[EventListenSymbol][evtName].add({
      handle: fuc,
      once: true,
    });
    return () => {
      this.off(evtName, fuc);
    };
  }
  /** 添加事件监听 */
  on(evtName: string, fuc: (evt: EventData) => void, once = false): () => void {
    this[EventListenSymbol][evtName] = this[EventListenSymbol][evtName] || new Set();
    this[EventListenSymbol][evtName].add({
      handle: fuc,
      once,
    });
    return () => {
      this.off(evtName, fuc);
    };
  }
  /** 取消事件监听 */
  off(evtName: string, fuc: any) {
    if (!this[EventListenSymbol][evtName]) {
      return;
    }
    this[EventListenSymbol][evtName].forEach(item => {
      if (item.handle === fuc) {
        this[EventListenSymbol][evtName].delete(item);
      }
    });
  }
  /** 抛出事件 */
  trigger(evtName: string, val: any, context?: any[]) {
    if (!evtName) {
      return;
    }
    if (this[InnerProp].isBlock) {
      this[EventCatchSymbol].add({ evtName, evtData: cloneDeep(val) });
      return;
    }
    // 带上自己的上下文, 构造新 context
    const newContext = Array.from(context || []);
    newContext.push(this[InnerProp].eventData);
    // 执行监听函数
    const actions = this[EventListenSymbol][evtName];
    if (actions) {
      actions.forEach(action => {
        const { handle, once } = action;
        try {
          handle.call(this, {
            name: evtName,
            data: val,
            context: newContext,
          });
        } catch (e) {
          console.error(e);
        }
        if (once) {
          actions.delete(action);
        }
      });
    }
    this[InnerProp].parent?.trigger?.(evtName, val, newContext);
  }
}
export default CustomEventNode;
```

## Pico开发者论坛
**<font style="color:rgb(51, 51, 51);">公有社区URL：</font>**

<font style="color:rgb(51, 51, 51);">国内线上：</font>[https://developer-cn.pico-interactive.com/community](https://developer-cn.pico-interactive.com/community)

<font style="color:rgb(51, 51, 51);">海外线上：</font>[https://developer-global.pico-interactive.com/community](https://developer-global.pico-interactive.com/community)

**<font style="color:rgb(51, 51, 51);">私有社区URL：（需要白名单账号，只有海外环境）</font>**

<font style="color:rgb(51, 51, 51);">海外线上：</font>[<font style="color:#117CEE;">http://developer-us.pico-interactive.com/ab7d03a4</font>](http://developer-us.pico-interactive.com/ab7d03a4)

### 管理页面的搭建
  使用arco-design的layout组件进行搭建

  管理页面中遇到的几个问题：

1. 页面加载慢，编辑某一列内容后重新获取数据时页面卡死，这个时候使用tooltip组件获取具体某一项中的数据，解决问题
2. 服务端写接口异步的解决方案

前端调用服务端写接口后得到服务端请求成功后调用读接口，拉取不到写入的数据。目前的解决方案是前端mock，settimeout300毫秒再获取数据

> 前端mock？
>
> 前端mock的意思是前端调用接口后，关于接口调用后产生什么效果由前端代码手动写变更，比如点赞场景，点赞后数值加1。
>
> 优点：
>
> 即时交互的体验，无延时
>
> 缺点：
>
> + 没有经过服务端返回的成功率验证，前端的修改不能保证落库，只是用户视觉展示
> + 开发维护成本高，服务处理的结果有一套逻辑，前端需要理解这个逻辑并且重写一份，增加开发成本，如果增加完备的处理，还是需要等服务结果反馈有新的交互链路告知用户，还会再增加成本
>
> 使用的场景：
>
> + 就及时反馈的用户体验要求很高的场景，比如点赞，如果等待接口返回再修改状态，那么用户可能点击后感受到一定的延迟，才有点赞效果触发
> + 用户行为允许非百分百的成功率，比如前端修提前改点赞状态，如果此次点赞行为并没有成功，用户不会骂娘。用户发现的时候可能觉得自己是不是记错了，或者再点一次。
> + 小局部修改：点赞状态相比于内容详情
>

### starling接入
starling就是字节自研的一个智能国际化翻译平台，实现多语言的转换，我们传统的国际化是通过手动写好国际化的文案文件并进行替换，starling接入之后会自动扫描项目中的文本，并自动替换为t方法，进行替换。我们可以直接在starling平台上对文案进行管理

>  starling_intl 是⼀款基于 Starling 的前端 i18n ⼯具，底层基于 i18next 框架实现。 i18next 是⽬前 市⾯上最活跃，经过多年打磨，插件⽣态最⼴泛的⼀款i18n⼯具。  
>
>  starling_client   动态拉取⽂案  
>
> [Starling ——国际化前端使用文档 副本.pdf](https://www.yuque.com/attachments/yuque/0/2023/pdf/2366100/1699843319246-c1f67a0f-1a33-469b-b215-a2c17e5e509e.pdf)
>

**主要的逻辑就是在App组件入口使用useState创建一个变量starlingInited，用于判断我们的starling是否初始化成功，在useEffect hook中间，会使用initStarling.then中去更新我们的starlingInited，这样就可以保证我们再使用i18n之前已经被初始化了**

**initStarling在对starling进行基本初始化之后，会返回一个promise，当他成功之后才会去执行initStarling.then，完成变量的替换**

<font style="color:rgb(51, 51, 51);">主要遇到的问题是i18n.init是一个异步的方法，我们需要保证在使用I18n实例之前，它已经被初始化，在初始化之前使用实例的时候会报错</font>![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697114746642-8631df73-45a0-4e9d-b983-00a9f6939e5f.png)

```javascript
import { I18n } from '@ies/starling_intl';      
import Starling from '@ies/starling_client';

// 初始化i18n实例
// 详细配置见：https://starling.bytedance.net/open/content/9163/111688
I18n.init({
 // ...一些配置
});
// 新建 Starling Client 实例并拉取文案
// 详细配置见：https://starling.bytedance.net/open/content/9163/111694
const starling = new Starling({
  // ...一些配置
})

const initStarling = starling.load().then((texts: any) => {
  // 方法介绍参考 https://www.i18next.com/overview/api
  I18n.addResourceBundle('当前语言', 'translation', texts);
  I18n.setLang('en');
  // ensure I18n init complete
  return new Promise(resolve => setTimeout(resolve));
});

const App = ({ Component, ...pageProps }: { Component: any }) => {
  const [starlingInited, updateStarlingInited] = useState(false);
  // i18n.init是一个异步的方法，我们需要保证在使用I18n实例之前，它已经被初始化
  useEffect(() => {
    initStarling.then(() => updateStarlingInited(true));
  });
  return (
    {!starlingInited ? (
      // 可以设置一个loading效果
      ) : (
      // 需要渲染的dom
      )
    }
  )
}
```

### 进入页面逻辑判断
![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697114807906-6ed52e77-b28f-4623-b340-bdcf1d8887c9.png)

### 通过cursor游标查询数据
## 社区中台组件库
### 组件化
#### 为什么要组件化？
<font style="color:rgb(51, 51, 51);">早期的页面是比较简单的，现在的网页内容动态化，依靠服务提供真实内容，交互性极强，交互反馈要求高，功能性越来越强，组件化可以很好的解决如下问题帮助我们开发</font>

+ <font style="color:rgb(51, 51, 51);">项目复杂度增加，一个页面处理的内容过多</font>
+ <font style="color:rgb(51, 51, 51);">重复性劳动多，效率低</font>
+ <font style="color:rgb(51, 51, 51);">质量差难以维护</font>

#### 组件的基本特征
1. <font style="color:rgb(51, 51, 51);">高内聚低耦合</font>
+ <font style="color:rgb(51, 51, 51);">影响范围可控，包含样式和逻辑</font>
+ <font style="color:rgb(51, 51, 51);">功能独立，与外界的连接点有限</font>
2. 标准的结构

<font style="color:rgb(51, 51, 51);">组件通常有以下几个部分：UI，attribute/property，method，life cycle，status</font>

    - <font style="color:rgb(51, 51, 51);">UI：一些容器组件是没有UI的</font>

<font style="color:rgb(51, 51, 51);">我们把 UI 主要分成两个部分，内容和样式。这样似乎与 HTML 和 CSS 分别对应上了，其与传统的开发有什么区别呢？区别就在于我们在上文提到的隔离。但是使用各种方式，比如在打包阶段做一些额外的处理，帮助我们做到隔离，通常按照标准的写法是不会对外部产生不可控的影响的。</font>

<font style="color:rgb(51, 51, 51);">举例：vue 的单文件组件，template 和 style 部分就对应了内容和样式，也可以描述为渲染和样式。template 限制了只能书写组件的内容，style 加上 scoped 配置。如下图，在渲染成具体的 dom 的时候，vue 会给对应元素加上唯一标志，并在选择器中带上这个标志。以这种方式来保证组件间样式的隔离。</font>![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697115070410-6d2bc3dc-8431-46c6-8979-8b619b9b5b1d.png)

    - <font style="color:rgb(51, 51, 51);">attribute/property，method，status：这四个部分与组件的功能逻辑紧密相关。attribute 与 property 是初始化时的配置，status 是运行时的内部状态变量，method 是提供的方法。从代码角度来看，组件内所有运行时内容都可以归到这几类中。</font>

> <font style="color:rgb(119, 119, 119);">为什么会有 attribute 与 property 两个部分用来描述配置呢？我们认为组件是对 HTML 元素的扩展，attribute 便是承接与 HTML 元素的设计。HTML 的元素在书写的时候可以添加 attribute，但是受限于形式 attribute 仅是字符串格式，因为我们是写在 html 文件中的。但是我们都应该有经验，对一个组件的配置不可能只有字符串的，比如，我们在使用 swiper 轮播组件时，我们可以配置轮播动画的时长，是否自动轮播等。这时候我们往往会使用 js 的形式，并传一个对象进去。这种通过 js 来配置组件时传的值，叫做 property。attribute 与 property 通常是有对应关系的。我的建议是不需要太关心他们的区别，比如，我们现在使用的 vue 和 react 实际就抹平了二者的差别，你可以说都是 property。比如 vue 的模板语法中，:attr="object" 加了冒号的属性内容就可以被自动解析。jsx 语法中 attr={js} 也是不再限于字符串。我们后面就不再区分 attribute, property，而是统一使用 attribute 来描述。</font>
>

<font style="color:rgb(51, 51, 51);">attribute 是组件的配置部分，描述这个组件会如何表现，其中有部分细节需要注意：</font>

        * <font style="color:rgb(51, 51, 51);">生效时机，仅初始化时生效还是实时生效。</font>
        * <font style="color:rgb(51, 51, 51);">外部配置与实际配置是否实现为强一致。</font>
    - <font style="color:rgb(51, 51, 51);">Life cycle：组件代码执行的时机，生命周期通常有, 创建, 挂载, 销毁前等。 vue 和 react 都设计了其生命周期.</font>

<font style="color:rgb(51, 51, 51);">为什么要有生命周期, 因为我们在设计好一个组件以及组件的功能时, 我们需要在一些特定的时候执行一些代码, 比如初始化动作, 获取数据动作等。 我们把做这些动作的时机整理后发现, 我们往往需要在创建的时候需要做一些动作, 在构建好组件的 dom 挂载到页面的时候需要做一些动作, 在销毁前需要做一些动作比如内存释放等。</font>

#### 什么是好的组件？
<font style="color:rgb(51, 51, 51);">组件使用人员角度</font>

    - <font style="color:rgb(51, 51, 51);">组件功能使用，功能不太强大，也不会太小</font>
    - <font style="color:rgb(51, 51, 51);">好的API文档</font>
    - <font style="color:rgb(51, 51, 51);">使用简单，易于理解</font>
    - <font style="color:rgb(51, 51, 51);">API不频繁发生break变动</font>

<font style="color:rgb(51, 51, 51);">组件开发人员角度</font>

    - <font style="color:rgb(51, 51, 51);">组件易于阅读，可清晰了解其能力边界设计</font>
    - <font style="color:rgb(51, 51, 51);">可扩展功能迭代</font>
    - <font style="color:rgb(51, 51, 51);">历史债少，已经提供的能力不能轻易删除</font>

<font style="color:rgb(51, 51, 51);">如何判断是否要拆：</font>

    - <font style="color:rgb(51, 51, 51);">功能独立，与其他部分的耦合度小</font>
    - <font style="color:rgb(51, 51, 51);">功能稳定性（UI型的功能一般不稳定）</font>
    - <font style="color:rgb(51, 51, 51);">功能复用情况，想哪些场景可以用，现在有多少场景可用，未来可能有多少场景可用</font>
    - <font style="color:rgb(51, 51, 51);">功能复杂度高，复杂度高的组件才有组件化的价值</font>
    - <font style="color:rgb(51, 51, 51);">感觉能不拆时，先不拆</font>

<font style="color:rgb(51, 51, 51);">组件API设计时的注意点：</font>

    - <font style="color:rgb(51, 51, 51);">宜精不宜多</font>
    - <font style="color:rgb(51, 51, 51);">权限能收则收，减少透传设计</font>
    - <font style="color:rgb(51, 51, 51);">注意属性取名</font>
    - <font style="color:rgb(51, 51, 51);">不过度设计</font>

<font style="color:rgb(51, 51, 51);">如何提高自己的组件化能力？</font>

    - <font style="color:rgb(51, 51, 51);">学习前人经验，观察和思考社区组件的设计</font>
    - <font style="color:rgb(51, 51, 51);">理解业务，理解业务诉求，理解需求的最优价值的点，已经需求的稳定点和变化点</font>
    - <font style="color:rgb(51, 51, 51);">向后思考，思考未来发展的方向</font>
    - <font style="color:rgb(51, 51, 51);">review 设计，及时调整</font>

#### <font style="color:rgb(51, 51, 51);">组件化&模块化</font>
[组件化开发和模块化开发概念辨析 - Derek_Cheng - 博客园](https://www.cnblogs.com/yichenscc/p/9361856.html)		

<font style="color:rgb(51, 51, 51);">组件化就是把可以复用的、独立的、基础的、功能专一的代码封装到一个方法或者代码片段里，在未来需要的地方引入使用。用极少的代码实现之前相同的功能，避免了相同功能代码的复写，提高了开发的效率。在未来对该组件功能进行修改的时候只需要修改组件代码就可修改项目里所有的相同功能。组件化属于纵向分块，每个组件就像一个竖直的线永不相交。</font>

<font style="color:rgb(51, 51, 51);">模块化是为了单独实现某一功能模块进行封装的方法，一个模块里可能拥有n个基础组件搭配产生。模块化属于横向分块，每个模块像一条横向把n条竖直的线串联起来形成一个整体。</font>

### 打包优化
#### 优化本地开发
+ <font style="color:rgb(51, 51, 51);">加入Webpack Cache </font>[Cache | webpack](https://webpack.js.org/configuration/cache/)

<font style="color:rgb(51, 51, 51);">缓存生成的webpack模块和chunk，来改善构建速度，cache会在开发模式被设置成type:'memory'而且在生产模式中被禁用，</font>

    - <font style="color:rgb(51, 51, 51);">二次启动时间75s+ -> 2s+, 提高95%+</font>

```javascript
cache: devMode
    ? {
        type: 'filesystem',
        cacheDirectory: path.resolve(__dirname, '.webpack_cache'),
        buildDependencies: {
          config: [path.resolve(__dirname, 'webpack.config.js')],
        },
      }
    : false,
```

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697115665516-ec027743-55f7-4fda-9e52-62cb46b1cd95.png)

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697115705171-8d39ac5b-ff99-4e13-9dab-7e6de7508751.png)

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697115724073-b32d685e-6b08-42e7-b306-7df3a449f1f7.png)

+ HMR优化 [react-hot-loader](https://github.com/gaearon/react-hot-loader)

<font style="color:rgb(51, 51, 51);">React HMR支持，代码更新不触发导航栏级别刷新</font>

```javascript
// babel.config.json中配置
{
  "plugins": ["react-hot-loader/babel"]
}
const Demo = () => {
    console.log('.....');
    return (
        <Router>...</Router>
    )
}
export default hot(Demo)
```

+ UMD

UMD (Universal Module Definition)，就是一种javascript通用模块定义规范，让你的模块能在javascript所有运行环境中发挥作用。![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697115852596-c0b29152-ec45-4ab9-9c84-d8026b70387c.png)

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697115897352-639512d0-30e1-4aec-91e4-571b3daba2ec.png)



### 组件库接入starling
<font style="color:rgb(51, 51, 51);">在接入starling的项目中使用npm引入的未接入starling的组件库的时候，我们是扫描不到组件库中的文案的，所以应该在组件库中先完成starling的接入并且暴露出配置语言的属性供项目使用，比如arco-design中的locale。</font>

<font style="color:rgb(51, 51, 51);">需要注意的是将翻译的文案的文件直接保存在项目代码中，所以我们只需要在文案资源文件中添加新增的文案即可</font>

```javascript
文件所属位置：/src/locale/starling.ts
import { I18n } from '@ies/starling_intl';

export default (locale, lang = 'zh') =>
  // 创建starling实例 
  I18n.init({
    react: {
      useSuspense: false,
    },
    keySeparator: false,
    // 文案资源，我们选择将翻译文案静态保存在组件库项目中
    resources: {
      [lang]: { translation: locale },
    },
    fallbackLng: ['zh', 'en'],
    lng: lang, // 表示当前语言为【中文】
  });

文件所属位置：/src/locale/interface.ts

export interface Locale {
  [key: string]: string;
}

文件所属位置：/src/components/ConfigProvider/index.tsx

import starling from '@/locale/starling';
export interface ConfigProviderProps {
  /** 语言包 */
  locale?: Locale;
  /** 当前语言模式 */
  lang?: 'zh' | 'en';
}
/** 组件全局配置Provider */
const ConfigProvider: React.FC<CommunityConfigProviderProps> = ({ children, ...others }) => {
  const { lang, locale } = others;
  const [I18nReadly, setI18nReadly] = useState(false);

  useEffect(() => {
    starling(locale, lang).then(() => setI18nReadly(true));
  }, [lang, locale]);
  // 保证i18n实例初始化完成才渲染页面
  return <ConfigContext.Provider value={contextValue}>{I18nReadly ? children : null}</ConfigContext.Provider>;
};
```

### 代码规范
<font style="color:rgb(51, 51, 51);">因为我们是在做组件库，每个人的代码风格不一样，所以需要统一代码规范</font>

1. <font style="color:rgb(51, 51, 51);">提升协作效率</font>
2. <font style="color:rgb(51, 51, 51);">提升交付质量</font>
3. <font style="color:rgb(51, 51, 51);">有助于代码审阅</font>
4. <font style="color:rgb(51, 51, 51);">可降低维护成本</font>
5. <font style="color:rgb(51, 51, 51);">有利于团队成员养成代码规范的习惯</font>
+ <font style="color:rgb(51, 51, 51);">在.vscode/extensios.json文件中对于vscode的插件进行配置</font>
+ <font style="color:rgb(51, 51, 51);">代码缩进：统一使用两个空格，单行140作为代码缩进格式</font>![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697116115866-ba8eedbc-6cc1-4116-8572-2ed40477f232.png)
+ <font style="color:rgb(51, 51, 51);">命名</font>
    - <font style="color:rgb(51, 51, 51);">变量函数使用小驼峰camelCase</font>
    - <font style="color:rgb(51, 51, 51);">组件命名，类型定义，类名，枚举，以及枚举值使用PascalCase大驼峰</font>
    - <font style="color:rgb(51, 51, 51);">泛型使用单个大写字母</font><font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">T</font><font style="color:rgb(51, 51, 51);">等或</font><font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">PascalCase</font><font style="color:rgb(51, 51, 51);">（泛型参数较多易混淆的情况），不使用类型定义前缀（例如</font><font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">IDemoInterface</font><font style="color:rgb(51, 51, 51);">、</font><font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">EEnumDef</font><font style="color:rgb(51, 51, 51);">等）</font>
    - <font style="color:rgb(51, 51, 51);">常量/配置使用</font><font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">UPPER_SNAKE_CASE</font>
    - <font style="color:rgb(51, 51, 51);">文件/文件夹命名使用</font>
        * <font style="color:rgb(51, 51, 51);">组件文件夹命名 </font><font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">PascalCase</font>
        * <font style="color:rgb(51, 51, 51);">其它文件夹命名 </font><font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">kebab-case</font>
    - <font style="color:rgb(51, 51, 51);">请求中的路径、参数名、参数值使用</font><font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">camelCase</font><font style="color:rgb(51, 51, 51);">（如该参数与服务端数据绑定，直接沿用服务端词汇并转换为</font><font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">camelCase</font><font style="color:rgb(51, 51, 51);">，不单独取名）</font>
    - <font style="color:rgb(51, 51, 51);">组件导出名称以及组件属性接口名称</font>
        * <font style="color:rgb(51, 51, 51);">组件导出名称与组件文件夹一致</font>
        * <font style="color:rgb(51, 51, 51);">组件属性接口名称 </font><font style="color:rgb(51, 51, 51);background-color:rgb(243, 244, 244);">组件名称+Props</font>
+ <font style="color:rgb(51, 51, 51);">将文件代码拆分为不同的区块，各区块间使用空行分割；组件/函数中的代码逻辑同理，将类似的声明/处理逻辑放在一起，不同区块间使用空行隔开，以提升代码清晰度</font>
    - <font style="color:rgb(51, 51, 51);">文件内容分块规则建议如下：</font>
        1. <font style="color:rgb(51, 51, 51);">三方库依赖引入</font>
        2. <font style="color:rgb(51, 51, 51);">样式文件引入</font>
        3. <font style="color:rgb(51, 51, 51);">自定义组件引入</font>
        4. <font style="color:rgb(51, 51, 51);">杂项引入（类型定义、实用函数等）</font>
        5. <font style="color:rgb(51, 51, 51);">类型定义</font>
        6. <font style="color:rgb(51, 51, 51);">实用函数</font>
        7. <font style="color:rgb(51, 51, 51);">代码主体</font>
        8. <font style="color:rgb(51, 51, 51);">导出相关</font>

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697116209812-674d4cc0-36f0-4bc6-a1c1-62496b5a7f0f.png)

可以是.eslintrc.*文件的形式也可以是package.json文件中的eslintConfig字段的形式，eslint会自动查找并读取这两个文件

# Hytera
![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697116813075-a00f5c13-e70c-4faa-8ecb-ef696ab8e89c.png)

## 水印
防止警情档案泄密

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697260426327-e35acd66-d82e-484d-8462-59fb8af9cebb.png)![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697265763112-b26f474d-d8fe-4212-9507-61eb4eabd164.png)

使用水印实例的时候我们可以传入水印的数据，项目中使用的用户名，警号以及ip地址生成水印

水印实例的生成是通过canvas生成的：

创建canvas的标签元素并设置一些属性，比如宽高，然后获取2d的canvas上下文，设置我们水印的样式，通过[toDataUrl](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLCanvasElement/toDataURL)方法生成水印的data URI，然后将我们生成的data URI适用于background-image中的url实现水印的显示

**我们使用MutationObserver()方法监听我们生成的水印的元素是否发生变化，如果我们的水印被删除或者被修改了样式我们便删除当前的水印重新生成，我们还设置了定时器，每隔一段时间重新渲染我们的水印**

```javascript
/*
 * @Author: master
 * @Date: 2021-12-06 15:50:36
 * @LastEditTime: 2023-04-20 11:20:49
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

```

## 警情画像列表组件
![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697266461044-3e60024f-a32b-4970-a46f-bddd43df5a8d.png)

HYTPoliceInquiries组件为我们在项目中使用组件，HYTPoliceInquiries包括HYTSearch和HYTPoliceInquiriesList两个组件

**HYTPoliceInquiries组件**

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697362014151-7c7129f5-756c-4b90-abe4-f4037cb2a75a.png)

在使用HYTPoliceInquiriesList时用户可能会存在定制内容的需求，我们会在$scopedSlots中获取到所有来自插槽的配置内容，在HYTPoliceInquiriesList组件中，通过判断scopedSlots的属性是否等于对应的值来判断应该显示的内容

## 代码健壮性
1. 输入验证：始终对输入进行验证和过滤，确保它们符合预期的格式、范围和类型。这可以防止错误数据引发程序崩溃或产生意外结果。
2. 异常处理：使用适当的异常处理机制来捕获和处理意外情况。通过捕获异常并提供有用的错误消息，可以使程序在出现问题时更加优雅地处理错误，而不是崩溃或产生不可预期的结果。
3. 边界情况考虑：在编写代码时，要考虑一些边界情况，例如输入为零、为空或超出预期范围的情况。针对这些情况编写适当的代码逻辑和处理方式。
4. 日志记录：在关键部分添加适当的日志记录，以便能够跟踪程序的执行流程和状态。这有助于诊断问题和调试代码，以及在发生错误时提供有用的信息。
5. 单元测试：编写单元测试来验证代码的功能和正确性。通过编写全面的测试用例，可以在修改代码时及时发现潜在的问题，并确保程序在各种情况下都能正常工作。
6. 代码复审：请其他人（例如同事或代码审查者）仔细审查你的代码。他们可以提供不同的视角和建议，帮助你发现潜在的问题并提出改进意见。
7. 防御性编程：使用防御性编程技术，例如参数检查、错误处理和异常处理，来避免潜在的问题和漏洞。
8. 及时更新：保持代码库和依赖项的更新。及时应用安全补丁和更新，以减少潜在的漏洞和安全风险。
9. 使用最佳实践：遵循编程语言和框架的最佳实践指南。这些指南通常包括一些提高代码质量和健壮性的建议。
10. 持续改进：不断改进代码的健壮性和可维护性是一个持续的过程。通过积极的反馈循环、学习和修复问题，你可以不断提高代码的质量。

## 自动化部署
### 部署
> **软件部署**（英语：Software deployment）是为将一个软件系统投入使用而进行的所有活动，[[1]](https://link.juejin.cn/?target=https%3A%2F%2Fzh.wikipedia.org%2Fwiki%2F%25E8%25BD%25AF%25E4%25BB%25B6%25E9%2583%25A8%25E7%25BD%25B2%23cite_note-1)包括硬件配置、软件的安装、[环境变量](https://link.juejin.cn/?target=https%3A%2F%2Fzh.wikipedia.org%2Fwiki%2F%25E7%258E%25AF%25E5%25A2%2583%25E5%258F%2598%25E9%2587%258F)设置等。在一些机器上批量安装某一程序也称为软件部署，分为指派与发布两种类型。 ——《维基百科》
>

**部署即为将构建后的应用或者服务安装到目标环境，前端项目中的部署指的就是将打包好的静态资源文件放在服务器上，真实的服务器不能直接被外部网络访问，这时需要用到nginx的代理。**

### 手动部署
手动部署即是实现从一套源码转为一个线上访问的网站的过程

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697364692007-97e1c953-1ca6-423b-9205-8807d16045eb.png)

+ 构建：将本地代码进行构建，一般是npm run build
+ 连接服务器：使用FTP或SSH工具连接
+ 上传资源：将构建产物上传到对应的web目录

### 一个简单的"自动化"：脚本
```javascript
echo "安装依赖"
npm install

echo "开始编译"
npm run build

echo "开始上传到服务器"
scp -r ./dist/* root@xxx.xxx.xxx.xxx:/usr/local/webserver/nginx/html 

echo "部署完毕"
```

简单分析一下：

+ 1. 编译构建产物dist
+ 2.将产物dist上传到服务器web目录

执行脚本前需要将本地公钥上传到服务器，以实现ssh免登录

这样部署的缺点：

+ 无日志跟踪，出现问题不容易发现
+ 出现问题无法及时回滚

相比于上面这个脚本，实际的打包构建过程会稍微繁琐一下，且一般情况下的项目都需要版本控制管理，也就是gate。所以运行完脚本后还需要commit一下再push到远程仓库。既然commit是必经步骤，那如果在commit之后让它自动拉取代码自动构建部署，是不是会更方便呢？

### CI/CD
CI指的是持续集成：指的是频繁的将代码集成到主干环境，可以让产品快速迭代。通常会针对项目代码进行自动化静态检测、单元测试、构建等活动。简单来说就是拉取代码库中的代码后执行意志定义好的操作脚本通过一系列编译操作构建出一个产物。

CD指的是持续交付和持续部署。持续交付指的是将产物部署在测试环境或交付给客户提前测试。持续部署指的是将产物部署在生产环境。

**自动化部署全流程**

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697367501465-10fad7ea-f0e5-4b3b-aee1-8eabb962fabd.png)

具体流程如下：

1. **提交代码：**代码提交push后，通过 webhook 机制去通知用于构建服务器。webhook 可以理解为git push之后会触发一个post请求，这个请求能提醒构建服务器有代码更新了。
2. **拉取代码：**构建服务器，把代码拉取下来，会进行静态代码检测，通常是进行一些快速的错误检查过程，比如语法检查，如果有错误就直接终止流程。基本的代码检查后进入构建环节。
3. **构建第一步：执行构建脚本，**可以理解为npm run build得到产物，产物会进行一些自动化测试安全检测压力测试等。
4. **构建第二步：**产物通过一些必要的测试之后，dockerfile + 产物 => docker镜像,此时构建完毕

> 为什么使用docker进行部署？
>
> + 环境统一：本地，线上使用相同版本的镜像
> + 更轻量且能快速部署：以前一个虚拟机至少需要几个G的磁盘空间，docker容器可以减少到MB级
> + 环境隔离：Docker可以隔离不同应用程序之间的相互影响
> + 一次构建，多次交付：当涉及到应用程序多副本部署或者应用程序迁移时，只要生成过一次镜像，在任何一台服务器都可以创建容器
>

5. **部署**：把docker镜像上传到 docker registry,最后把这个docker镜像部署到服务器

### 手动实现一个自动化部署
涉及的工具：

+ node、docker
+ 一个支持webhook的代码管理工具：github
+ 一台用于部署的云服务器
1. 配置webhook

Payload URL：服务器地址+端口

触发方式：push event![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697369294374-e28768b7-e478-4c06-8b1b-fbb3a8cc8757.png)

**push一下,发送请求但是没有连接上，说明配置好了，但是服务器没有进行响应**

> We couldn’t deliver this payload: failed to connect to host
>

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697369347589-eedab4f3-a114-4766-9b5f-2b92ce253d3e.png)

2. 服务器挂载一个http服务

用node简单实现一下，上传到云服务器并且开启

```plain
// server.js

const http = require("http")

http.createServer((req, res) => {
    console.log('接收到请求')
    if (req.method === 'POST' && req.url === '/') {
        //...
    }
    res.end('ok')
}).listen(3000,()=>{
    console.log('开启服务')
})
```

此时再进行一次push,会发现请求成功且有响应

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697369183005-faff60c5-8ab0-43f9-a757-84ae13305d73.png)

3. 创建Dockerfile

Dockerfile 是一个文本文件，用来配置 image

有了它，我们就可以根据build的产物去生成docker image了

```dockerfile
# 构建阶段
FROM node:lts-alpine as build-stage
WORKDIR /app
# 复制当前代码到/app目录
COPY . .
# 安装依赖
RUN yarn
# 打包
RUN yarn build

# nginx配置阶段
FROM nginx:stable-alpine as production-stage
# 把上一个阶段的产物放到nginx的web目录中
COPY --from=build-stage /app/dist /usr/share/nginx/html
# 暴露80端口
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

Dockerfile的两个阶段：

    - 构建阶段：基于node环境，安装依赖、打包构建，生产构建产物
    - nginx配置阶段：把上一个阶段的产物放到nginx的web目录中，并启动nginx服务
4. 完善node脚本服务
+ 拉取最新仓库代码

```javascript
const { execSync } = require("child_process");
// 拉取仓库最新代码
execSync(
  `git clone https://github.com/Harvey966/ci-test.git ${projectDir}`,
  {
    stdio: "inherit",
  }
);
console.log("拉取成功");
```

+ 创建 docker 镜像、销毁 之前的 docker 容器、创建 新 docker 容器

```javascript
// 创建 docker 镜像
execSync(`docker build . -t ${name}-image:latest `, {
  stdio: "inherit",
  cwd: projectDir,
});

// 销毁 docker 容器
execSync(
  `docker ps -a -f "name=^${name}-container" --format="{{.Names}}" | xargs -r docker stop | xargs -r docker rm`,
  {
    stdio: "inherit",
  }
);

// 创建 docker 容器
execSync(
  `docker run -d -p 8888:80 --name ${name}-container  ${name}-image:latest`,
  {
    stdio: "inherit",
  }
);
```

5. 最后测试

```plain
node server.js
```

git push测试一下

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697369182980-e933acac-5172-4f64-a965-f838e9af1d50.png)![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697369183033-6ffe884f-696f-4963-b20a-f52537b2093c.png)

### 一些CI/CD工具：
1. Github action

只需要指定workflow文件(yaml格式)

```yaml
name: Greeting from Mona
on: push

jobs:
  my-job:
    name: My Job
    runs-on: ubuntu-latest
    steps:
    - name: Print a greeting
      env:
        MY_VAR: Hi there! My name is
        FIRST_NAME: Mona
        MIDDLE_NAME: The
        LAST_NAME: Octocat
      run: |
        echo $MY_VAR $FIRST_NAME $MIDDLE_NAME $LAST_NAME.
```

2. Gitlab-CI

只需要指定.gitlab-ci.yml文件,git push后自动进入流水线按照配置的文件运行构建

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697369183218-837eb656-1249-4c12-acc5-473aa4e46244.png)

以上两个都是通过 yml 配置文件，**简化**webhook和 server.js 脚本的步骤

3. jenkins 

可视化的web界面，配置脚本和流程，使用起来特别方便

同样**简化**webhook和 server.js 脚本的步骤

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1697369182979-dcfbd81f-a850-4f47-a769-67447d724df5.png)

# 微前端
> [微前端-最容易看懂的微前端知识](https://zhuanlan.zhihu.com/p/141530392)
>
> [微服务是什么](https://zhuanlan.zhihu.com/p/66190538)
>
> [微前端-大型巨石应用的破局者 - 掘金](https://juejin.cn/post/7235547967113019429#heading-17)
>

## 概念
微前端的概念是由ThoughtWorks在2016年提出的，它借鉴了微服务的架构理念，核心在于将一个庞大的前端应用拆分成多个独立灵活的小型应用，每个应用都可以独立开发、独立运行、独立部署，再将这些小型应用融合为一个完整的应用，或者将原本运行已久、没有关联的几个应用融合为一个应用。微前端既可以将多个项目融合为一，又可以减少项目之间的耦合，提升项目扩展性，相比一整块的前端仓库，微前端架构下的前端仓库倾向于更小更灵活。

**采用微服务的原因主要在于：使用微服务架构来解耦服务间依赖**

**<font style="color:rgb(18, 18, 18);">微前端不是单纯的前端框架或者工具，而是一套架构体系</font>**

它主要解决了两个问题：

+ 随着项目迭代应用越来越庞大，难以维护。
+ 跨团队或跨部门协作开发项目导致效率低下的问题。

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1698590950079-7852390d-9dc0-4b99-b142-43aa45de6888.png)

优点： 

+ <font style="color:rgb(37, 41, 51);">可独立部署</font>
+ <font style="color:rgb(37, 41, 51);">将故障风险的粒度隔离到更小的范围</font>
+ <font style="color:rgb(37, 41, 51);">职责范围更窄，更加易于理解</font>
+ <font style="color:rgb(37, 41, 51);">拥有更小的代码库，有利于重构和替换</font>
+ <font style="color:rgb(37, 41, 51);">状态更易于预测，因为它不与其他系统共享状态</font>

<font style="color:rgb(37, 41, 51);">缺点：</font>

+ <font style="color:rgb(37, 41, 51);">冗余：各个团队需要建立维护自己的服务器，构建流程和持续集成的管道，可能还加载冗余的js/css</font>
+ <font style="color:rgb(37, 41, 51);">一致性：后端团队有独立的数据库，团队之间需要定期复制数据，一旦出现错误，容易引起数据不一致</font>
+ <font style="color:rgb(37, 41, 51);">异质性：技术栈可选择性多</font>
+ <font style="color:rgb(37, 41, 51);">更多的前端代码</font>

## 实现微前端的方案
![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1698591277624-ac0c6cba-ff68-41ca-87ff-3f219bf4e754.png)

1. 路由分发式微前端：<font style="color:rgb(37, 41, 51);">通过路由将不同的业务</font>**<font style="color:rgb(37, 41, 51);">分发到不同的、独立前端应用</font>**<font style="color:rgb(37, 41, 51);">上。其通常可以通过 HTTP 服务器的反向代理来实现，又或者是应用框架自带的路由来解决。</font>
+ <font style="color:rgb(37, 41, 51);">不同技术栈之间差异比较大，难以兼容、迁移、改造</font>
+ <font style="color:rgb(37, 41, 51);">项目不想花费大量的时间在这个系统的改造上</font>
+ <font style="color:rgb(37, 41, 51);">现有的系统在未来将会被取代</font>
+ <font style="color:rgb(37, 41, 51);">系统功能已经很完善，基本不会有新需求</font>
2. <font style="color:rgb(37, 41, 51);">iframe：通过iframe加载子应用。 通信可以通过postMessage进行通信</font>

优点： 

    - 简单
    - 隔离
    - 安全

缺点：

    - 布局约束
    - 性能开销
    - 破坏了语义化，对无障碍可访问性支持不好哦
    - 不利于seo，会当成2个页面
    - url 不同步。浏览器刷新 iframe url 状态丢失、后退前进按钮无法使用。
    - UI 不同步，DOM 结构不共享。想象一下屏幕右下角 1/4 的 iframe 里来一个带遮罩层的弹框，同时我们要求这个弹框要浏览器居中显示，还要浏览器 resize 时自动居中..
    - 全局上下文完全隔离，内存变量不共享。iframe 内外系统的通信、数据同步等需求，主应用的 cookie 要透传到根域名都不同的子应用中实现免登效果。
    - 慢。每次子应用进入都是一次浏览器上下文重建、资源重新加载的过程。
3. web component

将前端应用程序分解为自定义 HTML 元素。 基于CustomEvent实现通信  
Shadow DOM天生的作用域隔离

重写现有的前端应用，使用 Web Components 来完成整个系统的功能。

    - 被Web标准广泛支持
    - 自定义元素 shadow DOM 支持隔离
    - 引入了生命周期
    - shadow 兼容性支持度不够好

## 微前端组成
<font style="color:rgb(18, 18, 18);">当下微前端主要采用的是组合式应用路由方案，该方案的核心是“主从”思想，即包括一个基座（MainApp）应用和若干个微（MicroApp）应用，基座应用大多数是一个前端SPA项目，主要负责应用注册，路由映射，消息下发等，而微应用是独立前端项目，这些项目不限于采用React，Vue，Angular或者JQuery开发，每个微应用注册到基座应用中，由基座进行管理，但是如果脱离基座也是可以单独访问，基本的流程如下图所示：</font>

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1698591357129-2e7022dd-22bd-4529-be21-a84f6f24a613.png)

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1698591381772-60920ef8-7026-4d71-9331-49123d6a1ee9.png)

## <font style="color:rgb(18, 18, 18);">微前端的路由分发</font>
<font style="color:rgb(18, 18, 18);">作为微前端的基座应用，是整个应用的入口，负责承载当前微应用的展示和对其他路由微应用的转发，对于当前微应用的展示，一般是由以下几步构成：</font>

1. <font style="color:rgb(18, 18, 18);">作为一个SPA的基座应用，本身是一套纯前端项目，要想展示微应用的页面除了采用iframe之外，要能先拉取到微应用的页面内容， 这就需要</font>**<font style="color:rgb(18, 18, 18);">远程拉取机制</font>**<font style="color:rgb(18, 18, 18);">。</font>
2. <font style="color:rgb(18, 18, 18);">远程拉取机制通常会采用fetch API来首先获取到微应用的HTML内容，然后通过解析将微应用的JavaScript和CSS进行抽离，采用eval方法来运行JavaScript，并将CSS和HTML内容append到基座应用中留给微应用的展示区域，当微应用切换走时，同步卸载这些内容，这就构成的当前应用的展示流程。</font>
3. <font style="color:rgb(18, 18, 18);">当然这个流程里会涉及到CSS样式的污染以及JavaScript对全局对象的污染，这个涉及到隔离问题会在后面讨论，而目前针对远程拉取机制这套流程，已有现成的库来实现，可以参考</font>[import-html-entry](https://link.zhihu.com/?target=https%3A//www.npmjs.com/package/import-html-entry)<font style="color:rgb(18, 18, 18);">和</font>[system.js](https://link.zhihu.com/?target=https%3A//www.npmjs.com/package/system.js)<font style="color:rgb(18, 18, 18);">。</font>

<font style="color:rgb(18, 18, 18);">对于路由分发而言，以采用vue-router开发的基座SPA应用来举例，主要是下面这个流程：</font>

1. <font style="color:rgb(18, 18, 18);">当浏览器的路径变化后，vue-router会监听hashchange或者popstate事件，从而获取到路由切换的时机。</font>
2. <font style="color:rgb(18, 18, 18);">最先接收到这个变化的是基座的router，通过查询注册信息可以获取到转发到那个微应用，经过一些逻辑处理后，采用修改hash方法或者pushState方法来路由信息推送给微应用的路由，微应用可以是手动监听hashchange或者popstate事件接收，或者采用React-router，vue-router接管路由，后面的逻辑就由微应用自己控制。</font>

## <font style="color:rgb(18, 18, 18);">微前端的应用隔离</font>
<font style="color:rgb(18, 18, 18);">应用隔离问题主要分为主应用和微应用，微应用和微应用之间的JavaScript执行环境隔离，CSS样式隔离，我们先来说下CSS的隔离。</font>

**<font style="color:rgb(18, 18, 18);">CSS隔离</font>**<font style="color:rgb(18, 18, 18);">：当主应用和微应用同屏渲染时，就可能会有一些样式会相互污染，如果要彻底隔离CSS污染，可以采用CSS Module 或者命名空间的方式，给每个微应用模块以特定前缀，即可保证不会互相干扰，可以采用webpack的postcss插件，在打包时添加特定的前缀。</font>

<font style="color:rgb(18, 18, 18);">而对于微应用与微应用之间的CSS隔离就非常简单，在每次应用加载时，将该应用所有的link和style 内容进行标记。在应用卸载后，同步卸载页面上对应的link和style即可。</font>

**<font style="color:rgb(18, 18, 18);">JavaScript隔离</font>**<font style="color:rgb(18, 18, 18);">：每当微应用的JavaScript被加载并运行时，它的核心实际上是对全局对象Window的修改以及一些全局事件的改变，例如jQuery这个js运行后，会在Window上挂载一个</font><font style="color:rgb(18, 18, 18);background-color:rgb(245, 245, 245);">window.$</font><font style="color:rgb(18, 18, 18);">对象，对于其他库React，Vue也不例外。为此，需要在加载和卸载每个微应用的同时，尽可能消除这种冲突和影响，最普遍的做法是采用沙箱机制（SandBox）。</font>

<font style="color:rgb(18, 18, 18);">沙箱机制的核心是让局部的JavaScript运行时，对外部对象的访问和修改处在可控的范围内，即无论内部怎么运行，都不会影响外部的对象。通常在Node.js端可以采用vm模块，而对于浏览器，则需要结合with关键字和window.Proxy对象来实现浏览器端的沙箱。</font>

## <font style="color:rgb(18, 18, 18);">微前端的消息通信</font>
<font style="color:rgb(18, 18, 18);">应用间通信有很多种方式，当然，要让多个分离的微应用之间要做到通信，本质上仍离不开中间媒介或者说全局对象。所以对于消息订阅（pub/sub）模式的通信机制是非常适用的，在基座应用中会定义事件中心Event，每个微应用分别来注册事件，当被触发事件时再有事件中心统一分发，这就构成了基本的通信机制，流程如下图：</font>

![](https://cdn.nlark.com/yuque/0/2023/webp/2366100/1698592027571-01d38b94-9c0b-4d00-beff-d36e7acb58bc.webp)

<font style="color:rgb(18, 18, 18);">当然，如果基座和微应用采用的是React或者是Vue，是可以结合Redux和Vuex来一起使用，实现应用之间的通信。</font>

## <font style="color:rgb(18, 18, 18);">微前端有哪些框架</font>
<font style="color:rgb(18, 18, 18);">基于上述对微前端整体概念和理论的阐述，目前业界已经有不少框架来帮助开发者轻松的集成微前端架构，例如下面这些：</font>

+ [Mooa](https://link.zhihu.com/?target=https%3A//www.npmjs.com/package/mooa)<font style="color:rgb(18, 18, 18);">：基于Angular的微前端服务框架</font>
+ [Single-Spa](https://link.zhihu.com/?target=https%3A//www.npmjs.com/package/single-spa)<font style="color:rgb(18, 18, 18);">：最早的微前端框架，兼容多种前端技术栈。</font>
+ [Qiankun](https://link.zhihu.com/?target=https%3A//www.npmjs.com/package/qiankun)<font style="color:rgb(18, 18, 18);">：基于Single-Spa，阿里系开源微前端框架。</font>
+ [Icestark](https://link.zhihu.com/?target=https%3A//www.npmjs.com/package/icestark)<font style="color:rgb(18, 18, 18);">：阿里飞冰微前端框架，兼容多种前端技术栈。</font>
+ [Ara Framework](https://link.zhihu.com/?target=https%3A//www.npmjs.com/package/https%3A//ara-framework.github.io/website/docs/quick-start)<font style="color:rgb(18, 18, 18);">：由服务端渲染延伸出的微前端框架。</font>

<font style="color:rgb(18, 18, 18);">上面这些框架，笔者这里就不在过多延伸，各位读者感兴趣的话可以来亲自试试。</font>

### <font style="color:rgb(37, 41, 51);">single-spa</font>
+ 实现一套生命周期，在 load 时加载子 app，由开发者自己玩，别的生命周期里要干嘛的，还是由开发者造的子应用自己玩
+ 监听 url 的变化，url 变化时，会使得某个子 app 变成 active 状态，然后走整套生命周期
+ 子应用最关键的一步就是导出 bootstrap, mount, unmount 三个生命周期钩子。
+ 基于浏览器原生的事件系统，无框架耦合，全局开箱可用。
+ load 方法需要知道子项目的入口文件
+ 把多个应用的运行时集成起来需要项目间自行处理内存泄漏，样式污染问题
+ 没有提供父子数据通信的方式

![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1700460825956-8913c993-2c47-4ced-8b08-2571c7b87e80.png)

### qiankun
![](https://cdn.nlark.com/yuque/0/2023/png/2366100/1700621284060-96a7a847-cb02-47d7-8380-f9e11fb27831.png)

qiankun基于single-spa进行了二次开发

+ 主应用：只需要输入子应用的html入口
+ 子应用：<font style="color:rgb(37, 41, 51);">与single-spa基本一致，导出了三个生命周期函数</font>
+ <font style="color:rgb(37, 41, 51);">js沙箱</font>

> 沙箱隔离（Sandbox），<font style="color:rgb(37, 41, 51);">和浏览器沙箱一样，js沙箱能将不同子应用间的状态相互隔离。为了保证应用能够稳定的运行且互不影响，需要提供安全的运行环境，能够有效地隔离、收集、清除应用在运行期间所产生的副作用。</font>
>

proxy沙箱，它将window上的所有属性遍历拷贝生成一个新的fakewindow对象，紧接着使用proxy代理这个fakewindow，用户对<font style="color:rgb(37, 41, 51);">window操作全部被拦截下来，只作用于在这个fakeWindow之上。vm沙箱最大的好处就是适用于多子应用实例并行存在的情况，其本质就是创建出多个proxy实例，每个子应用被打包后的代码类似于一段IIFE自调用函数</font>

```javascript
class ProxySanbox {
  constructor() {
    this.running = false
    const fakeWindow = Object.create(null)
    this.proxy = new Proxy(fakeWindow, {
      get(target, key) {
        if (!this.running) {
          return window[key]
        }
        return key in target ? target[key] : window[key]
      },
      set(target, key, value) {
        target[key] = value
        return true
      }
      // 修改不再操作window属性
    })
  }
  active() {
    if (!this.running) this.running = true
  }
  inactive() {
    this.running = false
  }
}
const sanbox1 = new ProxySanbox()
const sanbox2 = new ProxySanbox()
sanbox1.active()
sanbox2.active()
sanbox1.proxy.a = 100
sanbox2.proxy.a = 100
console.log('sanbox1.proxy.a=', sanbox1.proxy.a)
console.log('sanbox2.proxy.a=', sanbox2.proxy.a)
sanbox1.inactive()
sanbox2.inactive()
sanbox1.proxy.a = 200
sanbox2.proxy.a = 200
console.log('sanbox1.proxy.a=', sanbox1.proxy.a)
console.log('sanbox2.proxy.a=', sanbox2.proxy.a)
```

```javascript
// 降级处理
const fakeWindow1 = new Proxy(window, {
  get() { ... }
  set() { ... }
})
const fakeWindow2 = new Proxy(window, {
  get() { ... }
  set() { ... }
})
// 子应用1
((window) => {
    console.log(window)
}(fakeWindow1))
// 子应用2
((window) => {
    console.log(window)
}(fakeWindow2))
```

+ <font style="color:rgb(37, 41, 51);"> css样式隔离：</font>CSS样式隔离问题主要分为主应用和微应用，微应用和微应用之间，当主应用和微应用同屏渲染时，就可能会有一些样式会相互污染，如果要隔离CSS污染，也有很多常见的实现方式。我们通常的做法是约定 css 前缀的方式来避免样式冲突，即各个子应用使用特定的前缀来命名 class，或者直接基于 css module 方案写样式。对于一个全新的项目，这样当然是可行，但是通常微前端架构更多的目标是解决某些现有+遗产项目的接入问题。很显然遗产应用通常是很难有动力做大幅改造的。当然每种方式都有其特定的优缺点，下面列举几种常见的解决方案。
    - shadow dom：

缺点：

        * <font style="color:rgb(37, 41, 51);">浏览器兼容性不好，由于微前端多应用于B端PC，可以适当限制下用户浏览器</font>
        * <font style="color:rgb(37, 41, 51);">某些UI库中的组件会被动态地挂载到document上，例如antd中的Modal、ToolTip等等，这就导致Shadow DOM中对外部样式的修改并不会生效。</font>
    - <font style="color:rgb(37, 41, 51);">BEM规范：</font>
        * B：Block 一个独立的模块，一个本身就有意义的独立实体 比如：header、menu、container
        * <font style="color:rgb(37, 41, 51);">E：Element 元素,块的一部分但是自身没有独立的含义 比如：header title、container input</font>
        * <font style="color:rgb(37, 41, 51);">M：Modifier 修饰符，块或者元素的一些状态或者属性标志 比如：small、checked。 这种方式说到底还是需要在开发人员之间形成一套命名规范，而通常情况由于代码量的增加，通过人为的规范来约束也是不可靠的，这里就不再过多阐述。</font>
    - <font style="color:rgb(37, 41, 51);">Css Module：CSS Module和BEM规范的原理基本相同，本质上也是用来生成一个单一的类名，不同之处在于这个类名是由唯一的hash值组成，以此来避免类名的重复。但是如果团队中老旧的项目没有采用CSS Module的话，改造的成本还是不小的。</font>
    - css in js
    - [post css](https://www.postcss.com.cn/docs/postcss-architecture)：<font style="color:rgb(37, 41, 51);">使用postcss能为整体css添加一个外层的命名空间，在打包时添加特定的前缀，以此来避免类名的冲突。</font>

## <font style="color:rgb(18, 18, 18);">是否要用微前端</font>
<font style="color:rgb(18, 18, 18);">微前端帮助开发者解决了实际的问题，但是对于每个业务来说，是否适合使用微前端，以及是否正确的使用微前端，还是需要遵循以下一些原则：</font>

1. <font style="color:rgb(18, 18, 18);">微前端最佳的使用场景是一些B端的管理系统，既能兼容集成历史系统，也可以将新的系统集成进来，并且不影响原先的交互体验。</font>
2. <font style="color:rgb(18, 18, 18);">整体的微前端不仅仅是只将系统集成进来，而是整个微前端体系的完善，这其中就包括：  
</font><font style="color:rgb(18, 18, 18);">1)：基座应用和微应用的自动部署能力。  
</font><font style="color:rgb(18, 18, 18);">2)：微应用的配置管理能力。  
</font><font style="color:rgb(18, 18, 18);">3)：本地开发调试能力。  
</font><font style="color:rgb(18, 18, 18);">4)：线上监控和统计能力等等。  
</font><font style="color:rgb(18, 18, 18);">只有将整个能力体系搭建完善，才能说是整个微前端体系流程的完善。</font>
3. <font style="color:rgb(18, 18, 18);">当发现使用微前端反而使效率变低，简单的变更复杂那就说明微前端并不适用。</font>

# AIA微服务组成
<font style="color:rgb(38, 38, 38);">AIA系统由以下几个微服务组成</font>

+ <font style="color:rgb(38, 38, 38);">commandcenter.aia.web    前端服务</font>
+ <font style="color:rgb(38, 38, 38);">commandcenter.aia.alarm    警情中心服务</font>
+ <font style="color:rgb(38, 38, 38);">commandcenter.aia.knowledge    知识中心服务</font>
+ <font style="color:rgb(38, 38, 38);">commandcenter.aia.nlp_fusion    nlp融合服务</font>
+ <font style="color:rgb(38, 38, 38);">commandcenter.aia.nlp.service    nlp计算服务</font>
+ <font style="color:rgb(38, 38, 38);">commandcenter.aia.etl    etl数据同步服务</font>

<font style="color:rgb(38, 38, 38);">其中AIA中各容器的主要功能如下：</font>

+ **<font style="color:rgb(38, 38, 38);">web服务：</font>**

<font style="color:rgb(38, 44, 49);">提供AIA系统的页面访问能力，主要为警情数据分析的功能，包含警情查询和统计、警情警力上图分析、</font>

<font style="color:rgb(38, 44, 49);">话务数据的查询和统计分析、知识库查询、报告仓库、警情自动预警等功能界面，通过调用后端其他服务接口获取统计分析结果并展示成对应的图表或报表，通过调用SAP接口实时记录用户操作行为。</font>

+ **<font style="color:rgb(38, 38, 38);">alarm服务：</font>**
    1. <font style="color:rgb(38, 44, 49);">通过调用smp的接口获取组织机构、字典等基础数据，并通过监听activemq获取基础数据的变更信息。</font>
    2. <font style="color:rgb(38, 44, 49);">提供警情中心页面查询接口和实现，其中包括动态投影、时空分析、警情画像、分析统计、警情挖掘、话务分析、报告仓库、自动预警等模块。</font>
    3. <font style="color:rgb(38, 44, 49);">通过任务调度组件，定时将警情数据和话务数据从aia数据库同步数据到ElasticSearch，定时计算警情预警，定时进行风险模型评估。</font>
+ **<font style="color:rgb(38, 38, 38);">etl服务：</font>**
    1. <font style="color:rgb(38, 44, 49);">将icc接警单数据和话务坐席等数据从icc数据库增量抽取并经过清洗后同步至aia数据库。</font>
    2. <font style="color:rgb(38, 44, 49);">将vcs处警单、反馈单数据、当事人数据、证据单数据等从vcs数据库增量抽取并经过清洗后同步至aia数据库。</font>
+ **<font style="color:rgb(38, 38, 38);">knowledge服务：</font>**
    1. <font style="color:rgb(38, 44, 49);">知识查询服务</font>
    2. <font style="color:rgb(38, 44, 49);">知识管理服务，其中包括编辑、删除、新增、导入等功能</font>
+ **<font style="color:rgb(38, 38, 38);">nlp-fusion服务：</font>**
    1. <font style="color:rgb(38, 44, 49);">封装了nlp-service的能力，通过将nlp-service的接口进行封装整合，统一对其他服务提供接口。</font>
+ **<font style="color:rgb(38, 38, 38);">nlp-service服务：</font>**
    1. <font style="color:rgb(38, 44, 49);">根据警情文本提取警情等级。</font>
    2. <font style="color:rgb(38, 44, 49);">根据警情文本提取模型标签。</font>
    3. <font style="color:rgb(38, 44, 49);">根据警情文本识别实体内容</font>

# <font style="color:rgb(38, 44, 49);">驾考宝典</font>
驾考系统之后主要分为管理系统和用户端两部分 

管理系统主要实现的功能就是题目，驾校的增删改查，图片上传还有查询； 

用户端的话主要就是顺序答题和模拟答题功能的实现  

## 登录
用户进入页面，再created函数中判断本地是否存储了账号以及密码，如果有的话回显在输入框，用户输入账号密码，点击登录，此时判断当前用户是否勾选记住密码框，如果选择了记住密码的话，则在本地存储信息。发送登陆请求时，我会对响应数据及进行拦截，获取后端生成的当前用户的token，然后对之后的每一次请求设置Authorization:’Bearer’+token，这样的话对之后进入系统的每一次请求就有权限了

### 记住密码：
在登陆表单中添加记住密码勾选框，methods中定义方法，判断用户是否勾选记住密码框，如果点击，则在本地存储中存储登录信息，再登陆中调用该函数，created函数中判断本地是否存储了账号以及密码，如果有的话回显在输入框

### 图片上传
我是用element-ui组件库中的upload实现的这个题目上传，由于我们上传题目的话是需要携带token的，由于我们在登录的时候就已经将这个token进行了本地保存，所以在upload组件中设置请求头：headers时，向本地存储中获取token，然后进行携带

### 图片懒加载：
在登录管理系统时，会获取到所有的题目，由于管理员登陆之后是不可能一次性看到所有题目的，如果一次性获取所有图片资源的话时间过长，会影响用户体验，我们设置图片懒加载之后会减少无效资源的加载，防止并发加载的资源过多会阻塞js的加载

实现：

**引入了intersectionapi，（构造函数）观察元素是否可见，因为我每页只显示五张图片，所以我预设的是一次性加载10张图片，因为每道题都有自己的题号，所以利用intersectionobserver** **api每隔10个题号做监听，判断该部分10道题是否进入可视区域。通过判断每个被监听元素的isIntersecting属性来判断是否进入到可视区域，进入到可视区域就将data-src属性赋值给src**

将页面上的图片的src属性设置为空字符串，而图片的真实路径设置在data-original属性中，当页面滚动的时候监听scroll事件，在scroll事件的回调中，判断我们的懒加载的图片是否进入可视区域，如果图片在可视区域内，则将图片的src属性值设置为data-original的值。我们需要知道窗口显示区的高度innerHeight，然后是图片到视窗上边的距离getBoudingClientRect().top，但是这种方法的话，scroll事件密集发生，计算量比较大，性性能消耗比较多。

### 顺序答题，模拟答题
顺序答题获取所有题目：

当选择框选中时获取选中的值，点击确认的时候，判断其是否正确，正确的话显示为绿色，错误的话为红色，当点击上一题或者下一题的时候重置样式，调用vuex定义好的方法切换题目

模拟答题

也是选中的值，当点击确认的时候不再改变样式，直接变为下一题，如果正确，正确题目数加1，错误的话，错误的加1 ，点击交卷的时候将错误题目数传给后台，然后获取响应数据中的分数并显示，并将本次答题时间以及成绩记录下来，可以再考试记录中查看。

