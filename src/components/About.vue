<template>
    <div class="about">
        <div class="about__icon">
            <Contact />
        </div>

        <h1 class="about__title">{{ title }}</h1>
        <span class="about__sub-title">{{ subTitle }}</span>
        <div class="about__body read-more" :class="{ 'read-more--active': open }">

            <slot></slot>

            <button @click="open = !open" class="read-more__button">
                <span>
                    {{ open ? 'Read Less' : 'Read More' }}
                    <Indicator class="indicator" />
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
        return {
            open: false
        }
    },
    methods: {
        expand: function () {

        }
    },
    components: {
        Contact, Indicator
    }
}
</script>

<style lang="scss" scoped>
.about {
    position: relative;
    padding: 0 10px 0 40px;
    margin-left: -15px;
    margin-right: -15px;

    &__icon {
        position: absolute;
        left: 10px;
        top: 0px;
    }

    &__title {
        font-weight: bold;
        font-size: 22px;
        display: block;
        margin-bottom: 2px;
    }

    &__sub-title {
        color: #4C4C4C;
        display: block;
        margin-bottom: 16px;
    }

    &__body {

    }

}

.read-more {
    position: relative;
    overflow: hidden;
    max-height: 100px;
    margin-bottom: 30px;
    padding-bottom: 20px;
    transition: max-height 1s ease;

    &:after {
        content: '';
        position: absolute;
        z-index: 1;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 66px;
        background: linear-gradient(to top, #fff 0, #fff 50%, rgba(0, 0, 0, 0) 100%);
        opacity: 1;
        transition: opacity .8s ease;
    }

    .indicator {
        transition: transform 1s ease;
    }

    &--active {
        max-height: 600px;

        &:after {
            opacity: 0;
        }

        .indicator {
            transform: rotate(180deg);
        }
    }

    &__button {
        position: absolute;
        bottom: 0px;
        left: 0;
        width: 100%;
        z-index: 2;
        font-size: 14px;
        border: 0;
        padding: 0;
        background: #fff;
        cursor: pointer;

        img,
        svg {
            vertical-align: middle;
        }

        span {
            display: inline-block;
            padding: 0px 5px;
            background: #fff;
            position: relative;
            z-index: 3;
        }

        &:after {
            position: absolute;
            left: 0;
            width: 100%;
            top: 10px;
            content: '';
            border-top: 1px solid #F1F1F1;
        }
    }

}
</style>
