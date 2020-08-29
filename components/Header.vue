<template>
  <div>
    <nav class="navbar navbar-expand-sm ohhisse-header">
      <img class="header-logo-img" src="/logo.png" />
      <!-- <div class="head-wrap01">
        <img src="https://placehold.jp/500x500.png" />
      </div>
      <div class="head-wrap02">
        <p class="sub-title">サイト内テキスト一括抽出ツール</p>
        <p class="navbar-brand">Oh hisse!</p>
      </div> -->
    </nav>
  </div>
</template>

<style>
.ohhisse-header {
  flex-flow: row nowrap;
  justify-content: flex-start;
  border-bottom: 1px solid #000;
}
.header-logo-img {
  display: block;
  width: auto;
  height: auto;
}
.head-wrap01 {
  margin-right: 1rem;
}
.head-wrap01 img {
  display: block;
  width: 100px;
}
.head-wrap02 {
  text-align: left;
}
.head-wrap02 .sub-title {
  font-size: 14px;
  margin: 0;
}
.head-wrap02 .navbar-brand {
  font-size: 40px;
  font-weight: bold;
  margin: auto;
}

@keyframes appear {
  0% {
    opacity: 0;
  }
}
</style>
