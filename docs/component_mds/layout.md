# Layout 布局

### 使用指南

在 page.json 中引入组件

```json
"usingComponents": {
  "w-row": "wuss-weapp/w-row/index",
  "w-col": "wuss-weapp/w-col/index",
}
```

### 图片演示

<img style="margin: 20px 0;" height="450px" src="../../resource/layout.jpg"/>



### 代码演示

```html
<w-pane title="Layout" desc="布局" />

<w-pane desc="Default" />
<view style="margin: 30px 0;">
	<w-row>
		<block wx:for="{{ 4 }}" wx:key="index">
			<w-col span="6">
				<view style="padding: 10px 0;font-size:14px;text-align:center;background: rgba(85,178,240,{{  index%2 == 0 ? .8 : .6 }});">
					span[6]
				</view>
			</w-col>
		</block>
	</w-row>
</view>

<view style="margin: 30px 0;">
	<w-row>
		<block wx:for="{{ 3 }}" wx:key="index">
			<w-col span="8">
				<view style="padding: 10px 0;font-size:14px;text-align:center;background: rgba(85,178,240,{{  index%2 == 0 ? .8 : .6 }});">
					span[8]
				</view>
			</w-col>
		</block>
	</w-row>
</view>

<view style="margin: 30px 0;">
	<w-row>
		<block wx:for="{{ 24 }}" wx:key="index">
			<w-col span="1">
				<view class="w-layout-col" style="padding: 15px 0;font-size:14px;text-align:center;background: rgba(85,178,240,{{  index%2 == 0 ? .8 : .6 }});">
          <view style="letter-spacing:0;font-size: 16rpx;">
            {{ index+1 }}
          </view>
				</view>
			</w-col>
		</block>
	</w-row>
</view>


<w-pane desc="Gutter" />
<view style="margin: 30px 0;">
	<w-row gutter="10">
		<block wx:for="{{ 4 }}" wx:key="index">
			<w-col span="6">
				<view style="padding: 10px 0;font-size:14px;text-align:center;background: rgba(85,178,240,{{  index%2 == 0 ? .8 : .6 }});">
					gutter[10]
				</view>
			</w-col>
		</block>
	</w-row>
</view>


<w-pane desc="Direction" />
<view style="margin: 30px 0;">
	<w-row direction="right">
		<block wx:for="{{ 2 }}" wx:key="index">
			<w-col span="6">
				<view style="padding: 10px 0;font-size:12px;text-align:center;background: rgba(85,178,240,{{  index%2 == 0 ? .8 : .6 }});">
					dirction[right]
				</view>
			</w-col>
		</block>
	</w-row>
</view>



<w-pane desc="Offset" />
<view style="margin: 30px 0;">
	<w-row>
		<block wx:for="{{ 2 }}" wx:key="index">
			<w-col span="6" offset="2">
				<view style="padding: 10px 0;font-size:12px;text-align:center;background: rgba(85,178,240,{{  index%2 == 0 ? .8 : .6 }});">
					offset[2]
				</view>
			</w-col>
		</block>
	</w-row>
</view>


<w-pane desc="Push" />
<view style="margin: 30px 0;">
	<w-row>
		<block wx:for="{{ 2 }}" wx:key="index">
			<w-col span="6" push="4">
				<view style="padding: 10px 0;font-size:12px;text-align:center;background: rgba(85,178,240,{{  index%2 == 0 ? .8 : .6 }});">
					push[4]
				</view>
			</w-col>
		</block>
	</w-row>
</view>


<w-pane desc="Pull" />
<view style="margin: 30px 0;">
	<w-row direction="right">
		<block wx:for="{{ 3 }}" wx:key="index">
			<w-col span="6" pull="2">
				<view style="padding: 10px 0;font-size:12px;text-align:center;background: rgba(85,178,240,{{  index%2 == 0 ? .8 : .6 }});">
					pull[2]
				</view>
			</w-col>
		</block>
	</w-row>
</view>
```

```javascript
```

```css
.w-layout-col::before {
  content: '';
  display: table;
  clear: both;
  overflow: hidden;
}
```

### API

#### Attribute 属性

##### Col
| 属性 |    说明    |  类型  | 默认值 |
| ---- | :--------: | :----: | -----: |
| offset | 栅格左侧的间隔格数，间隔内不可以有栅格	 | number | 0 |
| pull | 栅格向左移动格数 | number | 0 |
| push | 栅格向右移动格数 | number | 0 |
| span | 栅格占位格数，为 0 时相当于 display: none | number | 0 |

##### Row
| 属性 |    说明    |  类型  | 默认值 |
| ---- | :--------: | :----: | -----: |
| gutter | 栅格间隔	 | number | 0 |
| direction | 布局排列方式：[left/right]	 | string | left |

#### Event 事件

| 事件名 | 说明 | 参数 |
| ------ | ---- | ---- |



#### Slot 插槽

| 名称 | 说明 |
| ---- | ---- |


#### Class 自定义类名

| 类名       | 说明         |
| ---------- | ------------ |
| wuss-class | 根节点样式类 |
