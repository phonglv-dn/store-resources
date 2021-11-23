<template>
    <Dialog v-if="dialogIsShow" @myEvent="closeDialog"></Dialog>
    <div class="add-resource">
        <form @submit.prevent="submitResource()">
            <div class="form-control">
                <label for="title">Title</label>
                <input type="text" id="title" name="title" ref="titleInput">
            </div>
            <div class="form-control">
                <label for="description">Description</label>
                <textarea id="description" name="description" ref="descTextArea" rows="3"/>
            </div>
            <div class="form-control">
                <label for="link">Link</label>
                <input type="url" id="link" name="link" ref="linkInput">
            </div>
            <div>
                <button type="submit">Add Resources</button>
            </div>
        </form>
    </div>
</template>
<script>
import Dialog from "./Dialog.vue";
export default {
    name: 'AddResource',
    data() {
        return {
            dialogIsShow: false,
        }
    },
    components: {
        Dialog
    },
    inject: ['addResource'],
    methods: {
        submitResource() {
            const title = this.$refs.titleInput.value;
            const description = this.$refs.descTextArea.value;
            const link = this.$refs.linkInput.value;
            if (title === '' || link === '') {
                this.dialogIsShow = true;
                return;
            }
            this.addResource(title.trim(), description.trim(), link.trim());
        },
        closeDialog(data) {
            data == 'false' ? this.dialogIsShow = false : this.dialogIsShow = true;
        }
    }
}
</script>
<style scoped>
    .add-resource {
        border-radius: 12px;
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
        padding: 1rem;
        margin: 2rem auto;
        max-width: 40rem;
    }
    label {
        font-weight: bold;
        display: block;
        margin-bottom: 0.5rem;
    }
    input,
    textarea {
        display: block;
        width: 100%;
        font: inherit;
        padding: 0.15rem;
        border: 1px solid #ccc;
    }
    input:focus,
    textarea:focus {
        outline: none;
        border-color: #3a0061;
        background-color: #f7ebff;
    }
    .form-control {
        margin: 1rem 0;
    }
</style>