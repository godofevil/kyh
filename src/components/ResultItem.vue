<template lang="pug">
    .person
        .person__block.person__collapsed
            .person__name {{ person.name }}
            .person__showmore(@click="showMore = !showMore")
                span(v-if="!showMore") +
                span(v-else) -
        transition-group.person__block.person__expanded(name="fade")
            template(v-if="showMore")
                .person__image(:key="person.name")
                    <Loader v-if="!imageLoaded" />
                    img(@load="imageLoaded = true" :src="person.images.sm")
                .person__details(:key="person.id")
                    div Real name |
                        span   {{ person.biography.fullName }}
                    div Gender |
                        span   {{ person.appearance.gender }}
                    div Race |
                        span   {{ person.appearance.race }}
                    div Height |
                        span   {{ person.appearance.height[1] }}
                    div Weight |
                        span   {{ person.appearance.weight[1] }}
                    div Alignment |
                        span   {{ person.biography.alignment }}
                    div Work |
                        span   {{ person.work.base }}
                    div Occupation |
                        span   {{ person.work.occupation }}
                    div Connections |
                        span   {{ person.connections.groupAffiliation }}
                    div First appearance |
                        span   {{ person.biography.firstAppearance }}
</template>

<script>
    import Loader from '@/components/Loader'

    export default {
        data() {
            return{
                showMore: false,
                imageLoaded: false
            }
        },
        props: {
            person: {}
        },
        methods: {
            onImageLoad() {

            }
        },
        components: {
            Loader
        }
    }
</script>

<style lang="sass" scoped>
    @import './../sass/_colors'

    .fade-enter-active, .fade-leave-active
        transition: opacity .3s
    .fade-enter, .fade-leave-to
        opacity: 0

    .person
        justify-content: space-between
        background: #ffffffd1
        padding: 15px
        box-sizing: border-box
        border-radius: 5px
        color: $grey
        font-size: 1.4rem
        color: #000
        &__block
            display: grid
            grid-gap: 20px
        &__collapsed
            grid-template-columns: 1fr auto
        &__expanded
            grid-template-columns: auto 1fr
        &__name
            width: 70%
        &__showmore
            box-sizing: inherit
            font-size: 1.5rem
            cursor: pointer
            transition: color .3s
            &:hover
                color: darken($green, 20%)
        &__image
            align-self: center
        &__details
            font-size: 1.2rem
            color: darken($grey, 30%)
            & span
                color: #000
                font-size: 1.4rem

    @media (max-width: 960px)
        .controls
            grid-template-columns: auto
            &__button
                width: 100%
    @media (max-width: 640px)
        .person
            &__expanded
                grid-template-columns: auto
            &__image
                justify-self: center
</style>
