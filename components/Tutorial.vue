<template>
  <div>
    <!-- トップコンテンツ -->
    <section class="jumbotron text-center">
      <div class="container">
        <h1 class="jumbotron-heading">キカガクの商品紹介サイト</h1>
        <p class="lead text-muted">
          短期のハンズオンセミナーや長期コースなど様々な講座を用意しています。
        </p>
        <p>
          <a href="https://www.kikagaku.co.jp/" class="btn btn-primary my-2">
            キカガクのホームページ
          </a>
        </p>
      </div>
    </section>
    <main>
      <!-- 追加 -->
      <div class="album py-5">
        <div class="container">
          <div class="row">
            <!-- 商品カード -->
            <!-- v-for でループ処理 -->
            <a
              v-for="(product, index) in products"
              :key="index"
              class="col-md-4"
              :href="product.url"
              target="_blank"
            >
              <div class="card mb-4 box-shadow">
                <img
                  class="card-img-top"
                  :src="product.img"
                  data-holder-rendered="true"
                />
                <div class="card-body">
                  <p class="card-text">{{ product.name }}</p>
                  <div
                    class="d-flex justify-content-between align-items-center"
                  >
                    <small class="text-muted">{{ product.text }}</small>
                  </div>
                </div>
              </div>
            </a>
            <!-- ------- -->
          </div>
        </div>
      </div>
      <!-- -- -->
    </main>
  </div>
</template>

<script>
  // axios モジュールから読み込み
  import axios from 'axios'

  export default {
  //非同期処理を同期処理にするために async で宣言
  async asyncData() {
    // Stein の API URL / シート名
    const res = this.$axios.get('/api/sample')

    const { data } = await axios.get(url)
    return { products: data }
  },
  data() {
    const url =
      'https://api.steinhq.com/v1/storages/6395cbb3eced9b09e9a91e17/product'

    const { data } = axios.get(url)
    return {products: data}
  },
}
</script>



















