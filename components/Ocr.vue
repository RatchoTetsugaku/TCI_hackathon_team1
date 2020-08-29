<template>
  <form>
    <div class="form-group">
      <input
        type="email"
        class="form-control"
        id="exampleInputEmail1"
        aria-describedby="emailHelp"
        placeholder="URLを入力してください"
      />
    </div>
    <div class="">
      <input type="checkbox" id="exampleCheck1-1" />
      <label class="form-check-label" for="exampleCheck1-1">翻訳する</label>
    </div>

    <div class="lang-wrap">
      <div class="" style="display:inline">
        <input type="checkbox" id="exampleCheck2-1" />
        <label class="form-check-label" for="exampleCheck2-1"
          >日本語⇔英語</label
        >
      </div>
      <div class="" style="display:inline">
        <input type="checkbox" id="exampleCheck2-2" />
        <label class="form-check-label" for="exampleCheck2-2"
          >日本語⇔中国語</label
        >
      </div>
      <div class="" style="display:inline">
        <input type="checkbox" id="exampleCheck2-3" />
        <label class="form-check-label" for="exampleCheck2-3"
          >日本語⇔韓国語</label
        >
      </div>
    </div>

    <button type="submit" class="btn btn-primary">抽出する</button>
  </form>
</template>

<script>
import Tesseract from 'tesseract.js';

const STATUS_INITIAL = 0;
const STATUS_SAVING = 1;
const STATUS_SUCCESS = 2;
const STATUS_FAILED = 3;

export default {
  name: 'ocr',
  resource: 'OCR',
  data() {
    return {
      currentStatus: null,
      status: {},
      drawer: null,
    };
  },
  computed: {
    isInitial() {
      return this.currentStatus === STATUS_INITIAL;
    },
    isSaving() {
      return this.currentStatus === STATUS_SAVING;
    },
    isSuccess() {
      return this.currentStatus === STATUS_SUCCESS;
    },
    isFailed() {
      return this.currentStatus === STATUS_FAILED;
    },
    progress() {
      return Math.floor(this.status.progress * 100);
    },
  },
  methods: {
    ocr: function(event) {
      Tesseract.recognize(event.path)
        .progress((status) => {
          this.status = status;
        })
        .then((result) => {
          this.currentStatus = STATUS_SUCCESS;
          this.status = result;
        })
        .catch((error) => {
          this.currentStatus = STATUS_FAILED;
          this.status = error;
        });
    },
    reset() {
      this.currentStatus = STATUS_INITIAL;
      this.status = {};
    },
    save() {},
    drive() {},
    filesChange(fileList) {
      if (!fileList.length) return;
      this.currentStatus = STATUS_SAVING;
      this.ocr(fileList[0]);
    },
  },
  mounted() {
    this.reset();
  },
};
</script>

<style>
.lang-wrap {
  margin: 10px auto 40px;
}
.lang-wrap > div {
  margin-left: 20px;
}
.form-group input {
  width: 80%;
  margin: auto;
}
.btn-primary {
  background-color: #000;
  border-color: #000;
  border-radius: 0;

  color: #fff;
  max-width: 270px;
  width: 100%;
}
</style>
