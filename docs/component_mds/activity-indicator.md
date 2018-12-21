# ActivityIndicator 活动指示器

常用 loading

### 使用指南

在 page.json 中引入组件

```json
"usingComponents": {
  "w-indicator":"wuss-weapp/w-activity-indicator/index",
  "w-pane":"wuss-weapp/w-pane/index"
}
```


### 图片演示

<img style="margin: 20px 0;" height="450px" src="../../resource/activity-indicator.jpg"/>


### 代码演示

```html
<w-pane title="ActivityIndicator" desc="活动指示器" />

<w-pane desc="Type" />


<view class="cell" >
  <w-indicator show type="snake" />
  <w-indicator show type="diffusion" />
  <w-indicator show type="ball" />
  <w-indicator show type="catapult" />
</view>


<w-pane desc="Color" />

<view class="cell" >
  <w-indicator show color="#448ef6" type="snake" />
  <w-indicator show color="#75c2f6" type="diffusion" />
  <w-indicator show color="#ffe981" type="ball" />
  <w-indicator show color="#ff5da2" type="catapult" />
</view>


<w-pane desc="Size" />

<view class="cell" >
  <w-indicator show color="#35013f" size="small" type="snake" />
  <w-indicator show color="#b643cd" size="default" type="diffusion" />
  <w-indicator show color="#99ddcc" size="larger" type="ball" />
</view>

<w-pane desc="LoadingText" />

<view class="cell" >
  <w-indicator show text="Loading..." size="small" type="snake" />
  <w-indicator show text="Loading..." size="small" type="diffusion" />
  <w-indicator show text="Loading..." size="small" type="ball" />
</view>
```

```css
.cell {
  text-align: center;
  margin: 0 auto;
  display: flex;
  flex: 1;
  justify-content: center;
  flex-direction: column;
  flex-wrap: wrap;
  align-items: center;
}

.cell w-indicator {
  margin: 15px 0;
}
```

### API

#### Attribute 属性

| 属性 |    说明    |  类型  | 默认值 |
| ---- | :--------: | :----: | -----: |
| size | 指示器的大小,分别为[small/default/larger] | string | default |
| color | 动画的颜色 | string | rgb(252, 145, 83) |
| type | 动画类型，可选参数为[snake/diffusion/ball/catapult] | string | snake |
| text | 附加的文本内容 | string | - |
| textStyles | 附加的文本内容样式 | string | - |



#### Class 自定义类名

| 类名                    | 说明         |
| ----------------------- | ------------ |
| wuss-class              | 根节点样式类 |
| wuss-activity-indicator | loading 类   |
