<template>
    <tr :class="{ 'is-deleting': deleting }">
        <td>{{ path }}</td>
        <td>{{ date }}</td>
        <td>{{ size }}</td>
        <td class="text-right">
           
        </td>
    </tr>
</template>

<script>
export default {
    props: {
        date: { required: true },
        path: { required: true },
        size: { required: true },
        disk: { required: true },
        deletable: { required: true },
        deleting: { required: true },
    },

    computed: {
        downloadUrl() {
            const endpoint = '/nova-vendor/spatie/backup-tool/download-backup';

            return `${endpoint}?disk=${this.disk}&path=${this.path}`;
        },
    },
};
</script>

<style scoped>
.is-deleting td {
    color: var(--60);
}
</style>
