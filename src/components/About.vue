<template>
    <div class="about">
        <div class="about__icon">
            <Contact />
        </div>

        <h1 class="about__title">{{ title }}</h1>
        <span class="about__sub-title">{{ subTitle }}</span>
        <div class="about__body read-more">

            <slot></slot>

            <button class="read-more__button">
                <span>
                    {{ readMore }}
                    <Indicator />
                </span>
            </button>
        </div>
    </div>
</template>

<script>
import Contact from '../assets/images/contact-card.svg'
import Indicator from '../assets/images/indicator.svg'

export default {
    name: 'about',
    props: {
        title: String,
        subTitle: String,
        readMore: {
            type: String,
            default: 'Read more'
        }
    },
    data () {
        return {}
    },
    components: {
        Contact, Indicator
    }
}
</script>

<style scoped>

</style>
