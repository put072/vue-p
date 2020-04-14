<template>
  <div>
    <div class="about">
      <h1>101 Books {{ totalBooks }}</h1>
    </div>
    <br>
    <br>
    <Row style="padding:20px">
      <i-col v-for="(book, index) in books" :key="index" span="8" style="padding:20px">
        <Card :bordered="false" style="text-align: left;">
          <p slot="title">{{ index + 1 }}. {{book.book_name}}</p>
          <br>
          <a ghost :href="book.book_link_pdf" target="_blank">PDF</a>
        </Card>
      </i-col>
    </Row>
  </div>
</template>

<script>
export default {
  mounted () {
    this.$store.dispatch('getBooksFromApi')
  },
  computed: {
    books () {
      return this.$store.getters.getBooks
    },
    totalBooks () {
      let countBook = this.$store.getters.getTotals

      return (countBook > 0) ? `(${countBook})` : ''
    }
  }
}
</script>

