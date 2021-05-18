<template>
    <Modal>
        <div class="VideoPlayer">
            <iframe :src="url" 
            :title="title" 
            frameborder="0" 
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
            allowfullscreen></iframe>
        </div>
    </Modal>
</template>

<script>
import Modal from '../Modal/Modal';

export default {
    components: {
        Modal
    },
    props: {
        url: String,
        title: String
    }
}
</script>

<style lang="scss" scoped>
.VideoPlayer {
    position: relative;
    padding-bottom: 56.25%; /* 16:9 */
    height: 0;

    iframe, embed {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
    }
}
</style>