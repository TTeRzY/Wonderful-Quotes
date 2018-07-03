<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
        <add-new-quote @quoteAdded="newQuote"></add-new-quote>
        <app-quote-grid :quotes="quotes" @quteDeleted="deleteQuote"></app-quote-grid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">
                    Info: Click on a Quote to delete it!
                </div>
            </div>
        </div>
    </div>
</template>

<script>
  import QuoteGrid from './components/QuoteGrid.vue'
  import NewQuote from './components/NewQuote.vue'
  import Header from './components/Header.vue'

  export default {
    data() {
      return {
        quotes: [
          'Just a Quote to see something'
        ],
        maxQuotes: 10
      }
    },
    components: {
      appQuoteGrid: QuoteGrid,
      addNewQuote: NewQuote,
      appHeader: Header
    },
    methods: {
      newQuote(quote) {
        if (this.quotes.length >= this.maxQuotes) {
          return alert('Please delete quotes first!')
        }
        this.quotes.push(quote);
      },
      deleteQuote(index) {
        this.quotes.splice(index, 1);
      }
    }
  }
</script>

<style>
</style>
