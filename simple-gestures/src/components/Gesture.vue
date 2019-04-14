<template>
    <div class="gesture">
        <span>{{ gesture.from }} {{ gesture.type }} {{ gesture.to }}</span>
    </div>
</template>

<script>
export default {
    props: ['gesture'],
    data: function () {
        return {
            
        }
    }
}
</script>

<style scoped>

</style>
