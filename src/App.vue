<template>
    <div class="container">
    	<AppHeader :quoteCount="quotes.length" :maxQuotes="maxQuotes"/>
    	<NewQuote @quoteAdded="addQuote"/>
    	<QuoteGrid :quotes="quotes" @quoteDeleted="deleteQuote"/>
    	<div class="row">
    		<div class="col-sm-12 text-center">
    			<div class="alert alert-info">
    				Info: Click on a quote to delete it.
    			</div>
    		</div>
    	</div>
    </div>
</template>

<script>
	import QuoteGrid from './components/QuoteGrid.vue';
	import NewQuote from './components/NewQuote.vue';
	import AppHeader from './components/Header.vue';

    export default {
        data: function() {
        	return {
        		quotes: ['Sample quote to see something.'],
        		maxQuotes: 10	
        	}
        },
        components: {
        	QuoteGrid,
        	NewQuote,
        	AppHeader
        },
        methods: {
        	addQuote(quote) {
        		if (this.quotes.length >= this.maxQuotes) {
        			return alert('please delete quotes first');
        		}
        		this.quotes.push(quote)
        	},
        	deleteQuote(index) {
        		this.quotes.splice(index, 1);
        	}
        }
    }
</script>

<style>
</style>
