<template lang="pug">
    header.header
        .header__title Know Your Hero
        .header__subtitle superhero database
</template>

<style lang="sass" scoped>
    @import './../sass/_colors.sass'

    .header
        padding: 20px
        display: flex
        flex-direction: column
        align-items: center
        color: darken($grey, 30%)
        &__title
            font-family: 'Amatic SC', cursive
            font-size: 5vmax
            color: $green
        &__subtitle
            text-transform: uppercase
            font-size: 1vmax
            color: #grey
</style>
