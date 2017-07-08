<template>
    <form class="form" @submit.prevent="validateBeforeSubmit" v-if="!formSubmitted" action="">
        <slot name="description"></slot>

        <div class="form__group" :class="{ 'form--has-error' : errors.has('name') }">
            <label for="name" class="sr-only">Full name</label>
            <input type="text" v-model="name" v-validate="'required|alpha|min:3'" name="name" id="name" placeholder="Name" class="form__field">
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
            <textarea name="message" v-model="message" v-validate="'required|max_value:225'" id="message" placeholder="Message" class="form__field" cols="4"></textarea>
            <p class="text--danger form__error" v-if="errors.has('message')">{{ errors.first('message') }}</p>
        </div>

        <div class="form__group">
            <button type="submit" class="button__primary">Send</button>
        </div>
    </form>
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
            formSubmitted: false
        }
    },
    methods: {
        validateBeforeSubmit: function () {
            this.$validator.validateAll()

            console.log(this.errors.any())

            if (!this.errors.any()) {
                this.submitForm()
            }
        },
        submitForm: function () {
            this.$http({
                url: '/send-form',
                method: 'POST',
                data: {
                    name: this.name,
                    email: this.email,
                    message: this.message
                }
            }).then(() => {
                this.formSubmitted = true
                alert('form submitted!')
            }, () => {
                alert('Form submission failed!')
            })
        }
    },
    components: {}
}
</script>

<style scoped>
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
    }

    &__error {
        font-weight: bold;
        display: block;
        margin-bottom: 10px;
        padding-top: 10px;
    }

}
</style>
