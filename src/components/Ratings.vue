<template>
    <i class="fa fa-star" aria-hidden="true"></i>
    <i :class="[task.ratings >= 2 ? 'fa-star fa' : 'fa-star far']" aria-hidden="true"></i>
    <i :class="[task.ratings >= 3 ? 'fa-star fa' : 'fa-star far']" aria-hidden="true"></i>
    <i :class="[task.ratings >= 4 ? 'fa-star fa' : 'fa-star far']" aria-hidden="true"></i>
    <i :class="[task.ratings >= 5 ? 'fa-star fa' : 'fa-star far']" aria-hidden="true"></i>
</template>

<script>
export default {
    name: 'Ratings',
    props: {
        task: Object,
    },
}
</script>

<style>
.fa{
    color: rgb(230, 199, 29);
}
</style>