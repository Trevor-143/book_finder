<template>
    <footer>
        <div>
            <h3>By Arapu Trevor</h3>
            <h4>The Book Finder API</h4>
            <h5>&copy 2023</h5>
            <h6>{{ value }}</h6>
        </div>
    </footer>
</template>

<script>

export default {
    name: 'mainFooter',
    props: ['value']
}

</script>

<style scoped>
    div {
        color: #4d4d4d;
        display: flex;
        flex-direction: column;
        margin-bottom: 2rem;
        text-align: left;
        margin-top: 1rem;
        font-size: 13px;
    }
</style>