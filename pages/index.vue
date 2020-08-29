<template>
  <div class="container">
    <div>
      <Header />
      <div class="section01">
        <p>
          テキスト抽出サイト「Oh hisse！（オーエス）」は、<br />
          フォームにURLを入れるだけで、サイト内のテキストを一括抽出できるツールです。<br />
          <br />
          画像内のテキストも「それ引け！」と引っこ抜けるから、今までの手動抽出が嘘みたい。<br />
        </p>
      </div>

      <Ocr />

      <div class="section02">
        <p style="font-weight:bold;">このサイト内でできること</p>
        <p>
          ・サイトのURLをフォームに入力するだけで、サイト内のテキストデータを一括抽出<br />
          ・画像内のテキストと画像のファイル名も抽出可能<br />
          ・自動翻訳機能も搭載しているので、日本語→英語などの多言語化にも便利<br />
          ・「翻訳する」のチェックボックスを外せば、画像抽出のみの対応も可能<br />
          <br />
        </p>
      </div>

      <div class="footer-wrap">
        <p>oh-hisse!©tci.hackathon2020</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
@import url(//netdna.bootstrapcdn.com/font-awesome/3.2.1/css/font-awesome.css);
.section01 {
  margin: 50px auto;
}
.section02 {
  text-align: left;
  max-width: 610px;
  width: 80%;
  margin: 60px auto 80px;
}
.container {
  margin: 0 auto;
  min-height: 100vh;
  max-width: none;
  justify-content: center;
  align-items: center;
  text-align: center;
  padding: 0;
}
.links {
  padding-top: 15px;
}
.footer-wrap {
  border-top: 1px solid #000;
  margin: 20px 0 0;
}
.footer-wrap p {
  text-align: center;
  padding: 0.2em 0;
  margin: 0;
}
input[type='checkbox'] {
  display: none;
} /* to hide the checkbox itself */
input[type='checkbox'] + label:before {
  font-family: FontAwesome;
  display: inline-block;
}
input[type='checkbox'] + label:before {
  content: '\f096';
} /* unchecked icon */
input[type='checkbox'] + label:before {
  letter-spacing: 10px;
} /* space between checkbox and label */
input[type='checkbox']:checked + label:before {
  content: '\f046';
} /* checked icon */
input[type='checkbox']:checked + label:before {
  letter-spacing: 5px;
} /* allow space for check mark */
</style>
