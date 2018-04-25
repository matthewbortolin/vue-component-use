<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <app-new-quote @quoteAdded="newQuote"></app-new-quote>
    <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid> 
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Info: Click on a Quote to delete it!</div>
      </div>
    </div>
  </div>
</template>

<script>
  import Header from './components/Header.vue';
  import QuoteGrid from './components/QuoteGrid.vue';
  import NewQuote from './components/NewQuote.vue';

  export default {
    data () {
      return {
        quotes: ['Quote just to see something'],
        maxQuotes: 10
      }
    },
    methods: {
      // Add new quote to array
      newQuote(quote) {
        if (this.quotes.length >= this.maxQuotes) {
          alert("Please delete quotes before adding more");
        }
        else {
          this.quotes.push(quote); 
        }
      },
      // Delete quote from array
      deleteQuote(index) {
        this.quotes.splice(index, 1);
      }
    },
    components: {
      'app-quote-grid': QuoteGrid,
      'app-new-quote': NewQuote,
      'app-header': Header
    }
  }
</script>

<style>
</style>
