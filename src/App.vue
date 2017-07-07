<template>
    <div class="container container--shadow" id="app">

        <header>
            <Logo class="logo" />
            <button type="button" class="bookmark">
                <Star />
            </button>
        </header>

        <main id="main-content" class="main">
            <div class="about__image">
                <img :src="image" alt="David Hewitt portrait">
            </div>

            <about title="David Hewitt" subTitle="Web Developer">
                <p>
                    I am a dedicated, hardworking person who has accumulated a wealth of industry relevant skills. I aim to become part of a team at a reputable company where I can continue to pursue my passion for software development.
                </p>

                <p>
                    I work well within a team environment as well as working using my own initiative, and can offer solutions to difficult problems. I pride myself on my communication and leadership skills and a professional work ethic.
                </p>

                <p>
                    My current development background revolves heavily around JavaScript and PHP however, I also have an excellent working knowledge in many other coding languages and frameworks.
                </p>

                <p>
                    Free time outside of office hours is dedicated to help improve the tools and standards used by myself and others throughout the development community, I also improve my understanding through attendance of conferences and meet ups.
                </p>

                <p>
                    Reading and watching a variety of media based on all aspects of computing is a hobby and I also participate in sporting activities such as snowboarding, gym and football.
                </p>
            </about>

            <section>
                <h2>My Skills</h2>

                <accordion v-for="(skill, index) in skills" :key="index" :items="skill.items" :title="skill.title"></accordion>
            </section>

            <section>
                <h2>Education</h2>

                <school title="Queensbury Upper School" start="September 2005" end="September 2010"></school>
                <panel title="A2 Level Results" :items="a2Results"></panel>
                <panel title="BTEC First Results" :items="btecResults"></panel>
                <panel title="GCSE Results" :items="gcseResults"></panel>
                <school title="Priory Middle School" start="September 2001" end="September 2005"></school>
                <school title="Totternhoe Lower School" start="September 1996" end="September 2001"></school>
            </section>

            <section>
                <h2>Employment</h2>

                <timeline :items="timelineItems"></timeline>
            </section>

            <section>
                <h2>Contact</h2>

                <quick-links twitter="mosh1e" github="moshie"></quick-links>
                <contact-form>
                    <span class="form__description" slot="description">Like what you see? Get in touch below!</span>
                </contact-form>
            </section>
        </main>

        <footer class="footer">
            <span class="footer__body">David Hewitt</span>
        </footer>

    </div>
</template>

<script>
import image from './assets/images/david-hewitt.jpg'
import Logo from './assets/images/logo.svg'
import Star from './assets/images/star.svg'

import skills from './assets/content/skills.json'
import a2Results from './assets/content/a2-results.json'
import btecResults from './assets/content/btec-results.json'
import gcseResults from './assets/content/gcse-results.json'
import timelineItems from './assets/content/timeline-items.json'

import about from './components/About'
import accordion from './components/Accordion'
import school from './components/School'
import panel from './components/Panel'
import timeline from './components/Timeline'
import quickLinks from './components/QuickLinks'
import contactForm from './components/ContactForm'

export default {
    name: 'app',
    data () {
        return {
            image,
            skills,
            a2Results,
            btecResults,
            gcseResults,
            timelineItems
        }
    },
    components: {
        Logo,
        Star,
        about,
        accordion,
        school,
        panel,
        timeline,
        quickLinks,
        contactForm
    }
}
</script>

<style>

</style>
