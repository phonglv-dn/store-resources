<template>
    <div class="dialog" @click.stop="myEvent('false')">
        <div class="dialog__content">
            <div>
                <h2 class="dialog__title">Invalid Input</h2>
            </div>
            <div class="dialog__paragraph">
                <p class="dialog__desc">Unfortunately, at least one input value is invalid.</p>
                <p class="dialog__desc">Please check all inputs and make sure you enter at least a few characters into each input field.</p>
            </div>
            <div class="dialog__btn">
                <button @click.stop="myEvent('false')">Okay</button>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'Dialog',
    methods: {
        myEvent(data) {
            this.$emit('myEvent', data);
        }
    }
}
</script>
<style scoped>
    .dialog {
        position: fixed;
        width: 100%;
        height: 100vh;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        background: rgb(0, 0, 0, 0.5);

    }
    .dialog__content {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        max-width: 40%;
        background: white;
        border-radius: 12px;
        animation: fadeInDown 550ms ease-in-out;
    }
    .dialog__title {
        padding: 1rem;
        margin: 0;
        background-color: #3a0061;
        color: #fff;
        border-radius: 12px 12px 0 0;
    }
    .dialog__paragraph {
        padding: 1rem;
        font-weight: bold;
    }
    .dialog__btn {
        padding: 1rem;
        display: flex;
        justify-content: flex-end;
    }
    @keyframes fadeInDown {
        0% {
            opacity: 0;
            top: 0;
        }
        100% {
            opacity: 1;
            top: 50%;
        }
    }
</style>