# CSS アニメーション
画像が際立つ CSS アニメーションのご紹介です。アイキャッチ画像や本文中の画像、ランディングページの画像など、いろいろな画像に使えます。

※下記に表記してあるsampleは、すべてアニメーション1回

### 共通のHTML
```markup
<div class="img-wrap">
    <img>
</div>
```
#### 左から徐々に表示するアニメーション

```css
.img-wrap {
  overflow: hidden;
  position: relative;
}

.img-wrap:before {
  animation: img-wrap 2s cubic-bezier(.4, 0, .2, 1) forwards;
  background: #fff;
  bottom: 0;
  content: '';
  left: 0;
  pointer-events: none;
  position: absolute;
  right: 0;
  top: 0;
  z-index: 1;
}

@keyframes img-wrap {
  100% {
    transform: translateX(100%);
  }
}
```
#### 右から徐々に表示するアニメーション

```css
.img-wrap {
  overflow: hidden;
  position: relative;
}

.img-wrap:before {
  animation: img-wrap 2s cubic-bezier(.4, 0, .2, 1) forwards;
  background: #fff;
  bottom: 0;
  content: '';
  left: 0;
  pointer-events: none;
  position: absolute;
  right: 0;
  top: 0;
  z-index: 1;
}

@keyframes img-wrap {
  100% {
    transform: translateX(-100%);
  }
}
```

#### 画像の中心から、円形に広がるアニメーション。
（ IE と Edge では、アニメーションしません。）

```css
.img-wrap {
  animation: img-wrap 2s cubic-bezier(.4, 0, .2, 1);
}

@keyframes img-wrap {
  0% {
    clip-path: circle(0 at 50% 50%);
    -webkit-clip-path: circle(0 at 50% 50%);
  }
  100% {
    clip-path: circle(100% at 50% 50%);
    -webkit-clip-path: circle(100% at 50% 50%);
  }
}
```
ただし、 IE と Edge は `clip-path` に未対応です。いずれでもアニメーションはせず、ただ普通に画像が表示されます。


## 2 つの領域で異なるアニメーション
画像を 2 つの領域に分け、それぞれ異なるアニメーションにしてみます。 HTML は、これまでのものと変わりません。
```markup
<div class="img-wrap">
    <img>
</div>
```
#### 画像の上部は左から、下部は右から表示するアニメーション
```css
.img-wrap {
  overflow: hidden;
  position: relative;
}

.img-wrap:before,
.img-wrap:after {
  animation: 2s cubic-bezier(.4, 0, .2, 1) forwards;
  background: #fff;
  content: '';
  left: 0;
  pointer-events: none;
  position: absolute;
  right: 0;
  z-index: 1;
}

.img-wrap:before {
  animation-name: img-wrap-before;
  top: 0;
  bottom: 50%;
}

.img-wrap:after {
  animation-name: img-wrap-after;
  top: 50%;
  bottom: 0;
}

@keyframes img-wrap-before {
  100% {
    transform: translateX(100%);
  }
}

@keyframes img-wrap-after {
  100% {
    transform: translateX(-100%);
  }
}
```

#### 画像の左側は上から、右側は下から表示するアニメーション
```css
.img-wrap {
  overflow: hidden;
  position: relative;
}

.img-wrap:before,
.img-wrap:after {
  animation: 2s cubic-bezier(.4, 0, .2, 1) forwards;
  background: #fff;
  bottom: 0;
  content: '';
  pointer-events: none;
  position: absolute;
  top: 0;
  z-index: 1;
}

.img-wrap:before {
  animation-name: img-wrap-before;
  left: 0;
  right: 50%;
}

.img-wrap:after {
  animation-name: img-wrap-after;
  left: 50%;
  right: 0;
}

@keyframes img-wrap-before {
  100% {
    transform: translateY(100%);
  }
}

@keyframes img-wrap-after {
  100% {
    transform: translateY(-100%);
  }
}
```

## 3 つ以上の領域で異なるアニメーション

divを使えば画像を 3 つ以上の領域に分け、それぞれ異なるアニメーションを指定できます。

```markup
<div class="img-wrap">
    <div class="cover1"></div>
    <div class="cover2"></div>
    <div class="cover3"></div>
    <img>
</div>
```
```css
.img-wrap {
  overflow: hidden;
  position: relative;
}

.cover1,
.cover2,
.cover3 {
  animation: cover 2s cubic-bezier(.4, 0, .2, 1) forwards;
  background: #fff;
  height: 33.4%;
  left: 0;
  pointer-events: none;
  position: absolute;
  right: 0;
  z-index: 1;
}

.cover1 {
  top: 0;
}

.cover2 {
  animation-delay: .2s;
  top: 33.333333%;
}

.cover3 {
  animation-delay: .4s;
  top: 66.666666%;
}

@keyframes cover {
  100% {
    transform: translateX(100%);
  }
}
```
