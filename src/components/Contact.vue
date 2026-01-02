<script setup>
    import {ref} from 'vue'

    const form = ref({
        name: '',
        email: '',
        message: ''
    })

    // // TODO: SEND MESSAGE TO ME
    // const submit = () => {
    //     console.log(form.value)
    // }

</script>

<template>
    <div class="contact-section">
        <div class="contact-container">
            <h1 class="contact-title">Contact Me</h1>
            <form class="contact-form" name="contact" netlify @submit.prevent="submit">
                <input
                    type="text"
                    id="name"
                    v-model="form.name"
                    name="name"
                    placeholder="Full Name"
                />
                <input
                    type="text"
                    id="email"
                    v-model="form.email"
                    name="email"
                    placeholder="Email"
                />
                <textarea
                    type="text"
                    id="message"
                    class="message-input"
                    v-model="form.message"
                    name="message"
                    placeholder="Message"
                />
                <button class="contact-button" type="submit">Send Message</button>
            </form>
            
            <hr class="line-break"/>
            
            <div class="contact-links">
                <a href="https://www.linkedin.com/in/robeusanio/"><img src="/lnBug-White.png" title="LinkedIn" alt="LinkedIn Icon"/></a>
                <a href="https://github.com/robeusanio11"><img src="/github-mark-white.png" title="Github" alt="Github Icon"/></a>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .contact-section {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .contact-container {
        /* border-style: solid; */
        /* padding-left: 10rem;
        padding-right: 10rem; */
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 1rem;
        min-width: 45%;
        border-radius: 20px;
        background-color: rgba(255, 255, 255, .075);
    }

    .contact-title {
        color: white;
        font-weight: 400;
        text-shadow: 
            0 0 10px #6c2dffff,
            0 0 20px #6c2dffff
    }

    form {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        width: 100%;
    }

    form > input, form > textarea {
        width: 50%;
        padding: 1rem;
        margin: 0.75rem;
        border-radius: 20px;
    }

    .message-input {
        width: 70%;
        height: 10em;
    }

    form > button {
        width: 50%;
        padding: 1rem;
        margin: 1rem;
        margin-bottom: 0.5rem;
        border: 2px solid gray;
        border-radius: 20px;
        background-color: rgba(255, 255, 255, .075);
        color: rgb(200, 200, 200);

        transition:
            background-color 0.2s ease,
            transform 0.1s ease
    }

    form > button:hover {
        border-color: #470099ff;
        cursor: pointer;
    }

    form > button:active {
        background-color: rgba(255, 255, 255, .1);
        transform: scale(0.97);
    }

    hr {
        display: block;
        height: 1px;
        width: 95%;
        border: 0;
        border-top: 1px solid rgba(255, 255, 255, 0.2);
        margin: 1em;
        padding: 0;
    }

    .contact-links {
        margin: 0.5rem;
    }

    .contact-links > a {
        margin: 1rem;
    }
    
    img {
        width: 2rem;
        height: 2rem;
        margin: 0 2rem 0 2rem;
    }

</style>