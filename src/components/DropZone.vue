<script>
    import { ref } from 'vue';

    export default {
        name: "DropZone",
        setup() {
            const active = ref(false);

            const toggleActive = () => {
                active.value = !active.value;
            };

            return { active, toggleActive };
        }
    };
</script>

<template>
    <div 
        @dragenter.prevent="toggleActive" 
        @dragleave.prevent="toggleActive" 
        @dragover.prevent
        @drop.prevent="toggleActive"
        :class="{ 'active-dropzone': active }"
        class="dropzone"
    >
        <span>Drag and Drop</span>
        <span>OR</span>
        <label class="btn" for="dropzoneFile">Select File</label>
        <input type="file" name="dropzoneFile" id="dropzoneFile" class="dropzoneFile" accept=".xml">
    </div>
</template>

<style scoped>
    .dropzone {
        max-width: clamp(12.5rem, 12.5rem + 26.0417vw, 43.75rem);
        width: 100%;
        height: clamp(12.5rem, 12.5rem + 10.4167vw, 25rem);
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin: 1rem auto;
        row-gap: 1rem;
        border: 2px dashed var(--primary);
        color: #242424;
        transition: .3s ease all;
    }
    .active-dropzone {
        background: var(--primary);
        border: 2px dashed white;
        color: white;
    }
    .active-dropzone .btn {
        color: var(--primary);
        background: white;
    }
    .btn {
        padding: 8px 12px;
        border-radius: 0px;
        background-color: white;
        border: 1.5px solid var(--primary);
        color: var(--primary);
        transition: .3s ease all;
        cursor: pointer;
    }
    .btn:hover {
        color: white;
        background-color: var(--primary);
    }
    input {
        display: none;
    }
</style>