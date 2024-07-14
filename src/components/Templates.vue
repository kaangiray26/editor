<template>
    <div v-if="visible" class="overlay">
        <div class="templates-container">
            <ul>
                <li>Jekyll</li>
            </ul>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const visible = ref(false);

async function show() {
    visible.value = true;
}

async function hide() {
    visible.value = false;
}

defineExpose({
    show,
    hide
});
</script>