<template>
    <div v-if="!data || data.length == 0" class="text-center"><i class="fa fa-spinner fa-spin"></i> <span class="small">Загрузка...</span></div>
</template>

<script>
    module.exports = {
        props: {
            data: null
        }
    }
</script>