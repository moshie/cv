<template>
    <div class="school">
        <school class="school__icon" />
        <span class="school__title">{{ title }}</span>
        <span class="school__date">
            <time :datetime="startAttribute">{{ start }}</time> -
            <time :datetime="endAttribute">{{ end }}</time>
        </span>
    </div>
</template>

<script>
import school from '../assets/images/school.svg'

export default {
    name: 'accordion',
    props: {
        title: String,
        start: String,
        end: String
    },
    computed: {
        startAttribute: function () {
            return this.start
        },
        endAttribute: function () {
            return this.end
        }
    },
    components: {
        school
    }
}
</script>

<style lang="scss" scoped>
@import "../scss/helpers/clearfix";
.school {
    @extend .clearfix;
    padding-left: 30px;
    position: relative;
    display: block;
    margin-bottom: 25px;

    &:last-child {
        margin-bottom: 30px;
    }

    &__icon {
        position: absolute;
        left: 0px;
        top: 2px;
    }

    &__title {
        float: left;
        font-size: 17px;
        font-weight: bold;
        color: #000;
        margin-bottom: 3px;
    }

    &__date {
        float: left;
        clear: left;
        color: #4A4A4A;
        font-size: 12px;
    }
}
</style>
