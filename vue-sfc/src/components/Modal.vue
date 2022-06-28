<template>
    <div class modal="is-active">
    <div class="modal-background"></div>
    <div class="modal-content">
    <div class="box">
    <P>
    <slot> </slot>
    </P>
    <button class="modal-close" @click="$emit('close')"></button>
    </div></div></div>
</template>