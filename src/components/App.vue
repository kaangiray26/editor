<template>
    <div class="editor">
        <div class="settings-container">
            <button type="button" class="btn-title">editor</button>
            <button type="button" class="btn-settings">File</button>
            <button type="button" class="btn-settings">View</button>
            <button type="button" class="btn-settings ms-auto" @click="open_templates">Templates</button>
        </div>
        <div class="editor-container">
            <textarea ref="textarea" @input="onchange"></textarea>
        </div>
        <div class="information-container">
            <pre class="me-3 mb-0">wc: {{ word_count }}</pre>
            <pre class="mb-0">lc: {{ line_count }}</pre>
        </div>
    </div>
    <Templates ref="templates" />
</template>

<script setup>
import { ref } from 'vue'
import Templates from './Templates.vue';

const textarea = ref(null);
const templates = ref(null);

const word_count = ref(0);
const line_count = ref(0);

async function open_templates() {
    templates.value.show();
}

async function onchange() {
    const text = textarea.value.value;
    word_count.value = text.split(/\s+/).length;
    line_count.value = text.split(/\n/).length;
}
</script>