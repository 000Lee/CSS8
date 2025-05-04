#  CSS 애니메이션 & 변형 효과 정리

##  벤더 프리픽스 (Vendor Prefix)

브라우저별 실험적 속성 지원을 위해 사용

| 브라우저 | 접두사 |
|----------|--------|
| Chrome / Safari | `-webkit-` |
| Firefox         | `-moz-`    |
| Internet Explorer | `-ms-`  |
| Opera           | `-o-`      |

> 최신 브라우저에서는 대부분 불필요하지만, 과거 호환성 문제 해결용으로 사용

---

##  `transform` 변형 속성

###  2D 변형

| 기능 | 예시 |
|------|------|
| 이동 | `transform: translate(20px, 10px);` |
| x축 이동 | `translateX(50px)` |
| y축 이동 | `translateY(20px)` |
| 확대/축소 | `scale(0.7, 0.9)` |
| 회전 | `rotate(40deg)` (시계 방향) |
| 왜곡 | `skew(-25deg, -15deg)` |

추가 형태:
```css
transform: scaleX(2);
transform: rotateX(30deg); /* 3D도 가능 */
```

---

###  3D 변형

| 기능 | 예시 |
|------|------|
| 이동 | `translate3d(x, y, z)` / `translateZ(z)` |
| 확대 | `scale3d(x, y, z)` / `scaleZ(z)` |
| 회전 | `rotate3d(x, y, z, 각도)` |
| 원근감 | `perspective(300px)` → 부모 요소에 적용 |

```css
.container { perspective: 300px; }
.box:hover { transform: rotateZ(50deg); }
```

---

##  `transition` 속성

- **요소의 상태 변화에 부드러운 효과 부여**

###  기본 속성

| 속성 | 설명 |
|------|------|
| `transition-property` | 변화시킬 대상 (`width`, `height`, `all`) |
| `transition-duration` | 지속 시간 (`1s`, `2s`) |
| `transition-timing-function` | 진행 속도 패턴 (`linear`, `ease`, `ease-in`, `ease-out`, `ease-in-out`) |
| `transition-delay` | 지연 시간 |

###  축약형

```css
transition: property duration timing-function delay;
```

예시:
```css
.bg-tr {
  background-color: skyblue;
  transition: all 1s ease 1s;
}
.bg-tr:hover {
  background-color: blue;
}
```

 [Easing 예시 보기](https://easings.net/)  
 [Cubic Bezier 만들기](https://cubic-bezier.com/)

---

##  `animation` 속성

- 미리 정의된 키프레임에 따라 애니메이션 실행

###  키프레임 정의

```css
@keyframes 이름 {
  from { ... }
  to { ... }
}
```

###  기본 속성

| 속성 | 설명 |
|------|------|
| `animation-name` | 사용할 keyframes 이름 |
| `animation-duration` | 실행 시간 |
| `animation-delay` | 지연 시간 |
| `animation-iteration-count` | 반복 횟수 (`2`, `infinite`) |
| `animation-timing-function` | 속도 형태 |
| `animation-direction` | 방향 (`normal`, `reverse`, `alternate`, `alternate-reverse`) |

---

###  예시

```css
@keyframes shape {
  from { border: 1px solid transparent; }
  50% {}
  to { border: 1px solid #000; border-radius: 50%; }
}

.shape {
  animation: shape 2s ease-in-out;
}
```

---

###  여러 애니메이션 동시 적용

```css
animation: rotate 1.5s infinite, background 1.5s infinite alternate;
```

```css
@keyframes rotate {
  from { transform: perspective(120px) rotateX(0deg) rotateY(0deg); }
  50% { transform: perspective(120px) rotateX(-180deg); }
  to { transform: perspective(120px) rotateX(-180deg) rotateY(-180deg); }
}

@keyframes background {
  from { background-color: red; }
  50% { background-color: green; }
  to { background-color: blue; }
}
```

---

##  참고

- `transparent`: 투명색 지정
- `transform`, `animation`은 **레이아웃을 부드럽게 조작**할 때 매우 유용


