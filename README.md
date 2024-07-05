# 16. Tailwind CSS

여기서 나와있는 내용이 Tailwind CSS 의 전부는 아니다. 자주 쓰이는 것들만 정리해두었으므로, 한번 쭉 보고 익혀본 후, Tailwind CSS 공식문서를 여러번 참고해 필요한 기능들을 스스로 익혀보도록 하자.

# 1. font / text

## 1-1. 크기

사용: text-크기

ex) `text-3xl`

크기의 종류는 다음과 같다.

`xs` < `sm` < `lg` < `xl` < `2xl` < `3xl` < `4xl` < `5xl` < … < `9xl`

## 1-2. 굵기

사용: font-굵기

ex) `font-normal`

굵기의 종류는 다음과 같다.

`thin` : 100

`extralight` : 200

`light` : 300

`normal` : 400 (default)

`semibold` : 600

`bold` : 700

`extrabold` : 800

`black` : 900

외울 필요는 없는데, 커스텀 폰트 적용 시 보통 weight 를 숫자로 지정한다. 따라서 모든 굵기를 사용 가능한 게 아니라 정해진 숫자만 사용 가능.

예를 들면,

```jsx
const notoSansKr = Noto_Sans_KR({ subsets: ["latin"], weight: ["400", "700"] });
```

이 경우, 글자 크기는 기본 400 즉 `normal` 로 설정되고, 700 을 지정해놨으니 `font-bold` 를 사용해 굵기 변경 가능. 다른 클래스는 사용 불가.

## 1-3. 정렬

`text-left` : 왼쪽 정렬 (default)

`text-right` : 오른쪽 정렬

`text-center` : 가운데 정렬

`text-justify` : 양쪽 정렬

# 2. color

[https://tailwindcss.com/docs/customizing-colors](https://tailwindcss.com/docs/customizing-colors)

링크에선 default color palette 제공.

사용: 색상-넘버

ex) `blue-400` , `red-300`

넘버는 기본적으로 50, 100 - 900 (백단위), 950 까지 존재.

`500` 이 기본값이므로, 기본값을 쓸거면 숫자는 생략가능

글자 색깔이라면 `text-blue-400`

배경 색깔이라면 `bg-blue-400`

선 색깔이라면 `border-blue-400`

# 3. border

위치 축약

`t` : top

`b` : bottom

`l` : left

`r` : right

border-위치-rem, 또는 border-rem

ex) `border-b-2` , `border-3`

rem 은 0 - 8 까지 사용 가능

rem 대신 px 도 사용 가능하다. `[30px]` 식으로.

ex) `border-[30px]`

두께와 색상은 함께 쓸 수 없다. 분리해야한다.

ex) `className="border-b-1 border-black"`

⇒ 아랫쪽 선을 1rem 의 검은색으로 설정

CSS 와는 다르게, 순서를 지켜줘야한다. `border-1-b` 는 잘못되었다. `border-b-1` 이 맞다.

모서리 둥글게
사용: rounded-크기

ex) `rounded-lg`

크기의 종류는 다음과 같다.

`sm` < `md` < `lg` < `xl` < `full` (원형)

# 4. margin / padding

사용: m-rem, p-rem

ex) `m-2` , `p-3`

rem은 0 - 96 까지 0.5 단위로 사용 가능

왼쪽만 주고 싶다면 방향을 붙여주면 된다.

ex) `ml-2` , `pt-3`

방향보다 더 자주 쓰는게 y (상하), x (좌우)

ex) `my-2` , `px-3`

rem 외에 사용 가능한 것

`auto` : 자동

그러면 중앙 정렬할 때 자주 사용하는 CSS `margin: 0 auto` 는 어떻게 사용할까?

`my-0 mx-auto` 를 쓰면 된다.

# 5. height / width

사용: h-rem , w-rem

rem은 0 - 96 까지 0.5 단위로 사용 가능

ex) `h-1` , `w-2`

rem 대신에 이런 종류도 사용 가능

`full` : 부모 요소의 100%

`screen` : 화면 전체

`auto` : 내용의 크기에 따라 자동 결정

분수 : 부모 대비 사이즈 (`1/2` , `1/3` , `2/3` , `1/4` , `2/4` , `3/4`)

ex) `1/2` : 부모 대비 절반

최소, 최대

`min-h-screen` : 최소 높이를 화면의 전체 높이로 설정

`max-h-screen` : 최대 높이를 화면의 전체 높이로 설정

# 6. display / position

`block` : 블록

`inline` : 인라인

`inline-block` : 인라인 블록

`none` : 안보임

`relative` : 부모 기준

`absolute` : static 이 아닌 부모 기준

`fixed` : 고정

# 7. flex

`flex` : display 를 flex 로 지정

이후 다음 클래스 사용 가능

`flex-row` : (기본값)

`flex-col` : 정렬 방향 수직으로 변경

gab-숫자 : 요소간의 간격. 0부터 96 까지 0.5 단위로 사용 가능

ex) `gab-4`

`flex-grow` : 자동. 각 요소가 가능한 공간 채우기

`flex-grow-0` : 여분의 공간이 있어도 안 커지게 하기

`flex-grow-n` : 수동. 해당 비율만큼 커짐 (Holy Grail Layout 구현 시 사용)

`flex-shrink` : 자동. 여분 공간이 없을 때 필요에 따라 줄어듬

`flex-shrink-0` : 공간이 없어도 안 줄어들게 하기

`flex-grow-n` : 수동. 해당 비율만큼 작아짐.

`flex-n` : `grow` + `shrink` 즉, 해당 비율만큼 차지

`justify-center` , `items-center` : 중앙 정렬 시 사용

`items-end` : 요소의 끝에 배치

`flex-wrap` : 요소를 넘으면 줄바꿈

```
`align-content-center` : `flex-wrap` 과 함께 쓰며, 여러 행 사이의 간격이 조절되어 중앙 배치됨

```

`inline-flex` : `inline` + `flex` 즉, 박스는 `inline` 이라서 다른 요소와 한 줄에 배치되는데, 박스 안의 요소는 `flex`

## 8. Holy Grail Layout

## 8-1. flex 구현

```html
<div class="flex flex-col h-screen">
  <!-- Header -->
  <header class="flex flex-grow bg-blue-500 p-4 text-white">Header</header>

  <!-- Body -->
  <div class="flex flex-grow-4">
    <!-- Sidebar Left -->
    <nav class="flex flex-grow bg-green-500 w-64 p-4 text-white">Sidebar Left</nav>

    <!-- Main Content -->
    <main class="flex flex-grow-5 bg-white p-4">Main Content</main>

    <!-- Sidebar Right -->
    <aside class="flex flex-grow bg-green-500 w-64 p-4 text-white">Sidebar Right</aside>
  </div>

  <!-- Footer -->
  <footer class="flex flex-grow bg-blue-500 p-4 text-white">Footer</footer>
</div>

```

## 8-2. grid 구현

```html
<div class="grid h-screen grid-rows-6">
  <!-- Header -->
  <header class="row-span-1 bg-blue-500 p-4 text-white">Header</header>

  <!-- Body -->
  <div class="grid grid-cols-7 row-span-4">
    <!-- Sidebar Left -->
    <nav class="col-span-1 bg-green-500 w-64 p-4 text-white">Sidebar Left</nav>

    <!-- Main Content -->
    <main class="col-span-5 bg-white p-4">Main Content</main>

    <!-- Sidebar Right -->
    <aside class="col-span-1 bg-green-500 w-64 p-4 text-white">Sidebar Right</aside>
  </div>

  <!-- Footer -->
  <footer class="row-span-1 bg-blue-500 p-4 text-white">Footer</footer>
</div>

```

# 9. hover

사용 : `hover:클래스`

ex) `bg-blue-500 hover:bg-blue-700`

⇒ 평소엔 배경색이 blue-500 이지만, 커서 올리면 blue-700

# 10. 반응형클래스

사용: 반응형클래스:클래스

ex) `md:h-52`

⇒ 768px 이상일 때 높이 52rem

반응형클래스 목록

`sm:` - 640px <

`md:` - 768px <

`lg:` - 1024px <

`xl:` - 1280px <

`2xl:` - 1536px <