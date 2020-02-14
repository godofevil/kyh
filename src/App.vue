<template lang="pug">
    #app
        .container
            .wrap
                <Header />
                <Main />
</template>
<script>
    import Header from '@/components/Header'
    import Main from '@/components/Main'

    export default {
        name: 'App',
        components: {
            Header,
            Main
        }
    }
</script>
<style lang="sass">
    @import url('https://fonts.googleapis.com/css?family=Rubik&display=swap')
    @import url('https://fonts.googleapis.com/css?family=Amatic+SC&display=swap')

    *
        margin: 0
        padding: 0

    html
        scroll-behavior: smooth

    body
        font:
            family: 'Rubik', sans-serif
            size: 16px
        overflow-wrap: break-word
        background: url('./assets/bg.png') no-repeat #000 center top
        color: #fff
        position: relative

    .container
        max-width: 100%
        min-width: 320px

    .wrap
        max-width: 1170px
        min-width: 290px
        padding: 0 15px
        margin: 0 auto
</style>
