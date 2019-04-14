<template>
    <div>
        <form 
            class="form" 
            name="contact" 
            data-netlify="true"
            data-netlify-honeypot="bot-field" 
            @submit.prevent="validateBeforeSubmit"
            method="post"
        >
            <slot name="description"></slot>

            <div class="form__group" :class="{ 'form--has-error' : errors.has('name') }">
                <label for="name" class="sr-only">Full name</label>
                <input type="text" v-model="name" v-validate="'required|min:3'" name="name" id="name" placeholder="Name" class="form__field">
                <p class="text--danger form__error" v-if="errors.has('name')">{{ errors.first('name') }}</p>
            </div>

            <div class="form__group" :class="{ 'form--has-error' : errors.has('email') }">
                <label for="email" class="sr-only">Email</label>
                <input type="email" v-model="email" v-validate="'required|email'" name="email" id="email" placeholder="Email" class="form__field">
                <p class="text--danger form__error" v-if="errors.has('email')">{{ errors.first('email') }}</p>
            </div>

            <div class="form__group" :class="{ 'form--has-error' : errors.has('message') }">
                <label for="message" class="sr-only">
                    Message <small>(<span>{{ message.length }}</span> / <span>{{ maxLength }}</span>)</small>
                </label>
                <textarea name="message" v-model="message" v-validate="'required|max:225'" id="message" placeholder="Message" class="form__field" cols="4"></textarea>
                <p class="text--danger form__error" v-if="errors.has('message')">{{ errors.first('message') }}</p>
            </div>

            <div class="form__group">
                <button type="submit" class="button__primary">Send</button>
            </div>
        </form>
        <div class="form__success" v-if="formSubmitted">
            Thanks! I'll be in touch soon.
        </div>
        <div class="form__alert" v-if="submitError">
            Oops! Looks like something went wrong.
        </div>
    </div>
</template>

<script>
export default {
    name: 'contact-form',
    data () {
        return {
            name: '',
            email: '',
            message: '',
            maxLength: 225,
            submitError: false,
            formSubmitted: false
        }
    },
    methods: {
        validateBeforeSubmit: function (evt) {
            this.$validator.validateAll()

            if (!this.errors.any()) {
                this.submitForm(evt)
            }
        },
        submitForm: function (evt) {
            var data = {
                'form-name': 'contact-form',
                name: this.name,
                email: this.email,
                message: this.message
            }

            this.$http.post('/', this.encode(data), {
                headers: { 'Content-Type': 'application/x-www-form-urlencoded' }
            })
                .then(() => {
                    this.formSubmitted = true
                    this.submitError = false
                    console.log('form submitted!')
                }, () => {
                    this.submitError = true
                })
        }
    }
}
</script>

<style lang="scss" scoped>
.form {
    margin-bottom: 20px;

    @media print {
        display: none;
    }

    &__description {
        display: block;
        margin-bottom: 12px;
    }

    &__group {
        margin-bottom: 10px;
    }

    &__field {
        padding: 10px 10px;
        border-radius: 3px;
        border: 1px solid #AFAFAF;
        display: block;
        font-size: 14px;
        width: 100%;
    }

    textarea.form__field {
        resize: vertical;
        min-height: 80px;
        font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
    }

    &__error {
        font-weight: bold;
        display: block;
        margin-bottom: 10px;
        padding-top: 10px;
    }

    &__success {
        padding: 15px;
        color: green;
        border: 1px solid green;
        margin-bottom: 30px;
    }

    &__alert {
        padding: 15px;
        color: #A10F0F;
        border: 1px solid #A10F0F;
        margin-bottom: 30px;
    }

}
</style>
