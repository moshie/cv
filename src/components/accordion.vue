<template>
    <div class="accordion">
        <button @click="open = !open" class="accordion__title" :class="{ 'accordion--active': open }">
            {{ title }}
            <indicator class="indicator" />
        </button>
        <ul class="accordion__panel" v-show="open">
            <li class="accordion__item" v-for="item in items">
                {{ item.title }}
            </li>
        </ul>
    </div>
</template>

<script>
import indicator from '../assets/images/indicator.svg'

export default {
    name: 'accordion',
    props: {
        title: String,
        items: Array
    },
    data () {
        return {
            open: false
        }
    },
    components: {
        indicator
    }
}
</script>

<style scoped>
.accordion {
    border-top: 1px solid #F7F7F7;
    margin-left: -15px;
    margin-right: -15px;

    & + .accordion {
        border: 0;
    }

    &:last-child {
        margin-bottom: 30px;
    }

    &__title {
        background: transparent;
        border: 0;
        border-bottom: 1px solid #F7F7F7;
        padding: 10px 15px;
        font-weight: bold;
        display: block;
        font-size: 14px;
        width: 100%;
        text-align: left;

        img,
        svg {
            float: right;
            transition: transform .3s ease;
        }

        &.accordion--active img,
        &.accordion--active svg {
            transform: rotate(180deg);
        }

    }

    &__panel {
        background: #F7F7F7;
        display: none;

        .accordion--active + & {
            display: block;
        }
    }

    &__item {
        padding: 10px 15px;
        display: block;
        border-bottom: 1px solid #EFEFEF;

        img,
        svg {
            vertical-align: middle;
            margin-right: 6px;
        }
    }

}
</style>
