<template>
    <blog-post title="My journey with Vue" @enlarge-text="onEnlargeText">
    </blog-post>
</template>

<script>
export default {
    methods: {
        onEnlargeText(value){
            console.log(value)
        }
    }
}
</script>

