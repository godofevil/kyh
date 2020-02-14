<template lang="pug">
    .result
        <ResultItem v-for="person in searchResult" :key="person.id" :person="person" />
</template>

<script>
    import ResultItem from '@/components/ResultItem'

    export default {
        components: {
            ResultItem
        },
        props: {
            searchResult: Array
        }
    }
</script>

<style lang="sass" scoped>
    .result
        display: grid
        grid-template-columns: 1fr
        grid-row-gap: 10px        
</style>
