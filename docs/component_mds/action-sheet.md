# ActionSheet 操作菜单

### 使用指南

在 page.json 中引入组件

```json
"usingComponents": {
  "w-pane":"wuss-weapp/w-pane/index",
  "w-button":"wuss-weapp/w-button/index",
  "w-action-sheet":"wuss-weapp/w-action-sheet/index"
}
```

### 视频演示

<video style="margin: 20px 0;" height="450px" autoplay="true" loop="true" controls x5-playsinline="true" playsinline="true" webkit-playsinline="true" src="../../resource/action-sheet.mp4"
/>



### 代码演示

```html
<w-pane title="ActionSheet" desc="操作菜单" />

<w-pane desc="Default" />
<w-button
 type="info"
 data-key="1"
 bind:onClick="handleShow"
>
	{{ visible1 ? 'show' : 'hide' }}
</w-button>
<w-action-sheet
 data-key="1"
 visible="{{ visible1 }}"
 options="{{ items1 }}"
 bind:onChange="handleClick"
 bind:onClose="handleClose"
/>

<w-pane desc="Icon" />
<w-button
 type="info"
 data-key="2"
 bind:onClick="handleShow"
>
	{{ visible2 ? 'show' : 'hide' }}
</w-button>
<w-action-sheet
 data-key="2"
 visible="{{ visible2 }}"
 options="{{ items2 }}"
 bind:onChange="handleClick"
 bind:onClose="handleClose"
/>

<w-pane desc="MaskCancel = False" />
<w-button
 type="info"
 data-key="3"
 bind:onClick="handleShow"
>
	{{ visible3 ? 'show' : 'hide' }}
</w-button>
<w-action-sheet
 maskCancel="{{ false }}"
 data-key="3"
 visible="{{ visible3 }}"
 options="{{ items3 }}"
 bind:onChange="handleClick"
 bind:onClose="handleClose"
/>

<w-pane desc="ShowCancel = False" />
<w-button
 type="info"
 data-key="4"
 bind:onClick="handleShow"
>
	{{ visible4 ? 'show' : 'hide' }}
</w-button>
<w-action-sheet
 showCancel="{{ false }}"
 data-key="4"
 visible="{{ visible4 }}"
 options="{{ items4 }}"
 bind:onChange="handleClick"
 bind:onClose="handleClose"
/>

<w-pane desc="CancelText = 退出" />
<w-button
 type="info"
 data-key="5"
 bind:onClick="handleShow"
>
	{{ visible5 ? 'show' : 'hide' }}
</w-button>
<w-action-sheet
 cancelText="退出"
 data-key="5"
 visible="{{ visible5 }}"
 options="{{ items5 }}"
 bind:onChange="handleClick"
 bind:onClose="handleClose"
/>

<w-pane desc="Loading" />
<w-button
 type="info"
 data-key="6"
 bind:onClick="handleShow"
>
	{{ visible6 ? 'show' : 'hide' }}
</w-button>
<w-action-sheet
 cancelText="退出"
 data-key="6"
 visible="{{ visible6 }}"
 options="{{ items6 }}"
 bind:onChange="handleClick"
 bind:onClose="handleClose"
/>

<w-pane desc="插件手动调用" />
<w-button type="info" bind:onClick="handleClick2">ActionSheet.show()</w-button>
<w-action-sheet id="wuss-actionsheet" options="{{ items6 }}" bind:onChange="handleClick" bind:onClose="handleClose" />
```

```javascript
data: {
  visible: false,
  items1: [
    {
      text: '分享给朋友',
      type: 'share',
      openType: 'share',
    },
    {
      text: '分享到朋友圈',
      type: 'shareTimeLine',
      openType: 'share',
    },
  ],
  items2: [
    {
      text: '分享给朋友',
      type: 'share',
      icon: 'forward-o',
      openType: 'share',
    },
    {
      text: '分享到朋友圈',
      type: 'shareTimeLine',
      icon: 'share',
      openType: 'share',
    },
  ],
  items3: [
    {
      text: '分享给朋友',
      type: 'share',
      icon: 'forward-o',
      openType: 'share',
    },
    {
      text: '分享到朋友圈',
      type: 'shareTimeLine',
      icon: 'share',
      openType: 'share',
    },
  ],
  items4: [
    {
      text: '分享给朋友',
      type: 'share',
      icon: 'forward-o',
      openType: 'share',
    },
    {
      text: '分享到朋友圈',
      type: 'shareTimeLine',
      icon: 'share',
      openType: 'share',
    },
  ],
  items5: [
    {
      text: '分享给朋友',
      type: 'share',
      icon: 'forward-o',
      openType: 'share',
    },
    {
      text: '分享到朋友圈',
      type: 'shareTimeLine',
      icon: 'share',
      openType: 'share',
    },
  ],
  items6: [
    {
      text: '分享给朋友',
      type: 'share',
      openType: 'share',
    },
    {
      text: '分享到朋友圈',
      type: 'shareTimeLine',
      openType: 'share',
    },
  ],
},
handleClick(e) {
  const key = e.currentTarget.dataset.key;
  const item = e.detail;
  if(item.type === 'hide') return ActionSheet.hide({});
  if (key == 6) {
    this.setData(
      {
        [`items${key}[${item.key}].loading`]: true,
      },
      () => {
        setTimeout(() => {
          this.setData({
            [`items${key}[${item.key}].loading`]: false,
            [`visible${key}`]: false,
          });
        }, 2000);
      }
    );
  } else {
    this.setData({
      [`visible${key}`]: false,
    });
  }
},
handleClose(e) {
  const { key } = e.currentTarget.dataset;
  this.setData({ [`visible${key}`]: false });
},
handleShow(e) {
  const { key } = e.currentTarget.dataset;
  this.setData({ [`visible${key}`]: true });
},
handleClick2() {
  ActionSheet.show({
    options: [{text: 'ActionSheet.hide()',type: 'hide'}],
  })
},
onShareAppMessage: function (res) {
  if (res.from === 'button') {
    // 来自页面内转发按钮
    console.log(res.target)
  }
  return {
    title: '自定义转发标题',
    path: '/page/user?id=123'
  }
}
```

### API

#### Attribute 属性

| 属性 |    说明    |  类型  | 默认值 |
| ---- | :--------: | :----: | -----: |
| visible | 是否可见 | boolean | false |
| options | 当前传出的菜单列表    item属性有color,openType,loading,icon,iconSize,disabled,iconColor,text | array | []  |
| maskCancel | 点击遮罩是否可关闭 | boolean | false |
| showCancel | 是否展示取消按钮 | boolean | false |
| cancelText | 取消按钮文字 | string | 取消 |

#### Event 事件

| 事件名 | 说明           | 参数 |
| ------ | -------------- | ---- |
| onClose  | 取消回调       | ---- |
| onChange  | 值被改变时触发 |  e.detail.value |

#### Slot 插槽

| 名称   | 说明     |
| ------ | -------- |
| header | 头部插槽 |

#### Class 自定义类名

| 类名       | 说明         |
| ---------- | ------------ |
| wuss-class | 根节点样式类 |
