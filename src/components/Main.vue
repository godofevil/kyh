<template lang="pug">
    main.main
        div.controls
            input.controls__input(v-on:input="getData" v-model="searchRequest" type="search" autofocus="autofocus" placeholder="Hero name...")
        <Result v-if="searchRequest" :searchResult="searchResult"/>
        .error(v-if="showError") No hero found. Please specify another name.
</template>

<script>
    import Result from '@/components/Result'

    export default {
        name: 'Main',
        components: {
            Result
        },
        data() {
            return {
                searchRequest: '',
                searchResult: [],
                heroDB: {},
                showError: false
            }
        },
        methods: {
            async getData() {
                if (!this.heroDB.length) {
                    try {
                        let response = await fetch('https://cdn.rawgit.com/akabab/superhero-api/0.2.0/api/all.json');
                        this.heroDB = await response.json();
                    } catch(err) {
                        console.log(err);
                    }
                }
                this.searchRequest && this.search();
            }
        },
        computed: {
            search: function() {
                this.showError = false;
                let regexp = new RegExp(`${this.searchRequest.trim()}`, 'gi');
                this.searchResult = this.heroDB.filter(person => person.name.match(regexp));
                !this.searchResult.length ? this.showError = true : null;
            }
        }
    }
</script>

<style lang="sass" scoped>
    @import './../sass/_colors'

    .controls
        padding: 20px 0
        display: flex
        &__input
            padding: 5px
            font-size: 24px
            width: 100%
            height: 45px
            border-radius: 5px
            border: 1px solid $grey
            color: darken($grey, 30%)
            outline: 0
            transition: box-shadow .3s
            box-shadow: 0px 0px 23px 0px rgb(107, 224, 105)
    .error
        color: #fd5252
</style>
