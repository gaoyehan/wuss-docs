# Marquee 垂直滚动

### 使用指南

在 page.json 中引入组件

```json
"usingComponents": {
  "w-marquee": "wuss-weapp/w-marquee/index",
  "w-marquee-item": "wuss-weapp/w-marquee-item/index",
}
```

### 视频演示

<video style="margin: 20px 0;" height="450px" autoplay="true" loop="true" controls x5-playsinline="true" playsinline="true" webkit-playsinline="true" src="../../resource/marquee.mp4"
/>




### 代码演示

```html
<w-pane title="Marquee" desc="垂直滚动视图" />

<w-pane desc="Default" />

<w-button bind:onClick="handleClick1" type="info">+1</w-button>

<w-button bind:onClick="handleClick2" type="info">jump to 8</w-button>

<w-button bind:onClick="handleClick3" type="info">jump to 1</w-button>

<w-button bind:onClick="handleClick4" type="info">Next Item</w-button>

<view
 class=""
 hover-class="none"
 hover-stop-propagation="false"
>
	<w-marquee
	 bind:onChange="handleChange"
	 default-index="{{ 6 }}"
	 current-index="{{ currentIndex }}"
	>
		<w-marquee-item
		 bind:onClick="handleChange"
		 data-url="{{ item.url }}"
		 wx:for="{{ arr }}"
		 wx:key="item"
		 wuss-class="w-marquee-item"
		>
			<view style="background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAJIAAAAgCAYAAAD5eSHwAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6RTcxMDg1RDY4MTczMTFFNjk2MUNFQzY1NDU0Qjk3NUYiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6RTcxMDg1RDc4MTczMTFFNjk2MUNFQzY1NDU0Qjk3NUYiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDpFNzEwODVENDgxNzMxMUU2OTYxQ0VDNjU0NTRCOTc1RiIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDpFNzEwODVENTgxNzMxMUU2OTYxQ0VDNjU0NTRCOTc1RiIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PqQ66jEAAAmBSURBVHja7FsLbBRF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);background-size: 100% 100%;width: 73px;height: 16px;margin-right: 10px;" />
			<view
			 class=""
			 hover-class="none"
			 hover-stop-propagation="false"
			 style="font-size: 14px;"
			>
				{{ item.title }}
				{{ index }}
			</view>
		</w-marquee-item>
	</w-marquee>
</view>

<view
 class=""
 hover-class="none"
 hover-stop-propagation="false"
>
	<w-marquee
	 default-index="{{ 0 }}"
	 item-height="666.75"
	 current-index="{{ currentIndex }}"
	>
		<w-marquee-item
		 bind:onClick="handleChange"
		 data-url="{{ item.url }}"
		 wx:for="{{ arr }}"
		 wx:key="item"
		>
			<image style="width: 100%;height: 100%;display:block;margin: 0;padding: 0;" src="{{ item.imgSrc }}" />
		</w-marquee-item>
	</w-marquee>
</view>
```

```javascript
arr: [
  {
    title: '廊坊发生刑事案件',
    url: 'xxxx',
    imgSrc: 'http://img5.imgtn.bdimg.com/it/u=2918240254,2454690875&fm=26&gp=0.jpg',
  },
  {
    title: '小伙四万网购奔驰',
    url: 'xxxx',
    imgSrc: 'http://img3.imgtn.bdimg.com/it/u=3013567159,2250112086&fm=26&gp=0.jpg',
  },
  {
    title: '家人去世请假被拒',
    url: 'xxxx',
    imgSrc: 'http://img5.imgtn.bdimg.com/it/u=180988904,275450817&fm=26&gp=0.jpg',
  },
  {
    title: '于正秒删',
    url: 'xxxx',
    imgSrc: 'http://img2.imgtn.bdimg.com/it/u=1094944933,4065700883&fm=26&gp=0.jpg',
  },
  {
    title: '岳华去世',
    url: 'xxxx',
    imgSrc: 'http://img1.imgtn.bdimg.com/it/u=822102141,3878875172&fm=26&gp=0.jpg',
  },
  {
    title: '美将退出中导条约',
    url: 'xxxx',
    imgSrc: 'http://img4.imgtn.bdimg.com/it/u=1828593470,806721422&fm=26&gp=0.jpg',
  },
  {
    title: '范丞丞悼念粉丝',
    url: 'xxxx',
    imgSrc: 'http://img4.imgtn.bdimg.com/it/u=3939936779,946895769&fm=26&gp=0.jpg',
  },
  {
    title: '梅西骨折',
    url: 'xxxx',
    imgSrc: 'http://img4.imgtn.bdimg.com/it/u=3830398842,3489851318&fm=26&gp=0.jpg',
  },
  {
    title: '女子踩到男子',
    url: 'xxxx',
    imgSrc: 'http://img3.imgtn.bdimg.com/it/u=3348027003,368668260&fm=26&gp=0.jpg',
  },
  {
    title: '福原爱宣布退役',
    url: 'xxxx',
    imgSrc: 'http://img1.imgtn.bdimg.com/it/u=440375388,3364532017&fm=26&gp=0.jpg',
  },
  {
    title: '郭炳湘病逝',
    url: 'xxxx',
    imgSrc: 'http://img4.imgtn.bdimg.com/it/u=3133605357,944042545&fm=26&gp=0.jpg',
  },
],
currentIndex: null,
},
```

```css
.w-marquee-item {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  padding: 10px;
}

page {
  padding: 0;
}
```

### API

#### Attribute 属性

| 属性 |    说明    |  类型  | 默认值 |
| ---- | :--------: | :----: | -----: |
| interval | 过渡时间，默认为3s | number | 3000 |
| defaultIndex | 初始化后默认的索引 | number | 0 |
| itemHeight | 每个子节点(w-marquee-item)的高度 | number | 44 |
| currentIndex | 设置当前的激活索引 | number | 0 |

#### Event 事件

| 事件名 | 说明 | 参数 |
| ------ | ---- | ---- |
| onChange | 改变值后的回调 | e.detail.value |



#### Slot 插槽

| 名称 | 说明 |
| ---- | ---- |
| marquee-item | marquee的滚动子节点 |


#### Class 自定义类名

| 类名       | 说明         |
| ---------- | ------------ |
| wuss-class | 根节点样式类 |
