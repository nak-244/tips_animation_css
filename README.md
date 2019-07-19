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
