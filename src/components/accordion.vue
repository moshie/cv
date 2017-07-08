<template>
    <div class="accordion">
        <button @click="open = !open" class="accordion__title" :class="{ 'accordion--active': open }">
            {{ title }}
            <indicator class="indicator" />
        </button>
        <ul class="accordion__panel" v-show="open">
            <li class="accordion__item" v-for="(item, index) in items">
                <component :is="item.icon" :key="index"></component>
                {{ item.title }}
            </li>
        </ul>
    </div>
</template>

<script>
import indicator from '../assets/images/indicator.svg'

// JavaScript
import nodejs from '../assets/images/skills-icons/nodejs.svg'
import express from '../assets/images/skills-icons/express.svg'
import mongodb from '../assets/images/skills-icons/mongodb.svg'
import mocha from '../assets/images/skills-icons/mocha.svg'
import typescript from '../assets/images/skills-icons/typescript.svg'
import angular from '../assets/images/skills-icons/angular.svg'
import vue from '../assets/images/skills-icons/vue.svg'
import react from '../assets/images/skills-icons/react.svg'
import socketio from '../assets/images/skills-icons/socketio.svg'
import jquery from '../assets/images/skills-icons/jquery.svg'
import googlemaps from '../assets/images/skills-icons/googlemaps.svg'

// PHP
import laravel from '../assets/images/skills-icons/laravel.svg'
import codeigniter from '../assets/images/skills-icons/code-igniter.svg'
import wordpress from '../assets/images/skills-icons/wordpress.svg'

// .NET
import umbraco from '../assets/images/skills-icons/umbraco.svg'

// Hosting
import aws from '../assets/images/skills-icons/aws.svg'
import heroku from '../assets/images/skills-icons/heroku.svg'
import wpengine from '../assets/images/skills-icons/wpengine.svg'
import forge from '../assets/images/skills-icons/forge.svg'

// Tools
import webpack from '../assets/images/skills-icons/webpack.svg'
import gulp from '../assets/images/skills-icons/gulp.svg'
import grunt from '../assets/images/skills-icons/grunt.svg'
import browserify from '../assets/images/skills-icons/browserify.svg'
import office from '../assets/images/skills-icons/office.svg'
import adobe from '../assets/images/skills-icons/adobe.svg'
import git from '../assets/images/skills-icons/git.svg'

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
        indicator,

        // JavaScript
        nodejs,
        express,
        mongodb,
        mocha,
        typescript,
        angular,
        vue,
        react,
        socketio,
        jquery,
        googlemaps,

        // PHP
        laravel,
        codeigniter,
        wordpress,

        // .NET
        umbraco,

        // Hosting
        aws,
        heroku,
        wpengine,
        forge,

        // Tools
        git,
        webpack,
        gulp,
        grunt,
        browserify,
        office,
        adobe
    }
}
</script>

<style lang="scss" scoped>
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
