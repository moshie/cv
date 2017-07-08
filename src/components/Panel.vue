<template>
    <div class="panel">
        <button @click="open = !open" class="panel__header" :class="{ 'panel--active': open }">
            {{ title }}
            <indicator />
        </button>
        <ul class="panel__body" v-show="open">
            <li class="panel__item" v-for="item in items">
                <span v-html="item.subject"></span> - <strong class="text--danger">{{ item.grade }}</strong>
            </li>
        </ul>
    </div>
</template>

<script>
import indicator from '../assets/images/indicator.svg'

export default {
    name: 'panel',
    props: {
        title: String,
        items: Array
    },
    data () {
        return {
            open: true
        }
    },
    components: {
        indicator
    }
}
</script>

<style lang="scss" scoped>
.panel {
    margin-bottom: 20px;

    &__header {
        background: #F8F8F8;
        border: 1px solid #E4E4E4;
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

        &.panel--active img,
        &.panel--active svg {
            transform: rotate(180deg);
        }

    }

    &__body {
        border-left: 1px solid #E4E4E4;
        border-right: 1px solid #E4E4E4;
    }

    &__item {
        display: block;
        padding: 10px 15px;
        font-size: 14px;
        border-bottom: 1px solid #E4E4E4;
    }

}
</style>
