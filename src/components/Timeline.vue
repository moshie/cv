<template>
<ul class="timeline">
    <li class="timeline__item" v-for="item in items">
        <span class="timeline__title">{{ item.company }}</span>
        <span class="timeline__time">
            <time datetime="">{{ item.start }}</time> -
            <span v-html="item.end"></span>
        </span>
    </li>
</ul>
</template>

<script>
export default {
    name: 'timeline',
    props: {
        items: Array
    },
    data () {
        return {}
    },
    components: {}
}
</script>

<style lang="scss" scoped>
.timeline {
    margin-left: 10px;
    padding-left: 20px;
    margin-bottom: 30px;
    position: relative;

    &:after {
        content: '';
        position: absolute;
        left: -1px;
        top: 0;
        bottom: 20px;
        width: 1px;
        background: #E1E1E1;
    }

    &__item {
        position: relative;
        margin-bottom: 20px;

        &:after {
            position: absolute;
            left: -31px;
            z-index: 2;
            top: 0;
            content: '';
            width: 18px;
            height: 18px;
            border-radius: 50%;
            border: 1px solid #CECECE;
            background: #fff;
        }

        &:before {
            position: absolute;
            left: -25px;
            top: 6px;
            z-index: 3;
            content: '';
            width: 8px;
            height: 8px;
            background: #00A8FF;
            border-radius: 50%;
        }
    }

    &__title {
        display: block;
        font-weight: bold;
        margin-bottom: 2px;
    }

    &__time {
        display: block;
        padding-left: 15px;
        color: #3B3B3B;
    }

}
</style>
