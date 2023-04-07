<template>
    <div class="welcome">
        <h1>A summary of "{{this.$route.query.name}}".</h1>
        <div class="dash"></div>
    </div>
    <div class="info">
        <!-- <h3>detail {{ $route.params.id }}</h3>
        <h3>{{ this.$route.query.name }}</h3>  
        <h3>{{ this.$route.query.author }}</h3>-->
        <img :src="this.$route.query.image" :alt="this.$route.query.name">
        <div class="introInfo">
            <h3 class="name">{{ this.$route.query.name }}</h3>
            <h3 class="author">By {{ this.$route.query.author }}</h3>
            <h3 class="series">From the "{{ this.$route.query.series }}" series.</h3>
            <div class="tags">
                <h3 class="type">{{ this.$route.query.type }}</h3>
                <h3 class="lang">{{ this.$route.query.lang }}</h3>
                <h3 class="pages">{{ this.$route.query.pages }} pages</h3>
            </div>
        </div>
    </div>
    <div class="summary">
        <h2 class="snippet">Summary</h2>
        <p>{{ this.$route.query.summary }}</p>
    </div>
</template>

<script>

export default {
    
}
</script>

<style>
    .welcome {
        margin-top: 1rem;
    }
    .welcome h1 {
        font-size: 20px;
    }
    .dash {
        width: 100px;
        height: 5px;
        background-color: #000;
        margin-top: 0.5rem;
        border-radius: 10px;
    }
    .info {
        margin-top: 2rem;
        display: flex;
    }
    .info img {
        max-width: 250px;
        width: 100%;
        border-radius: 10px;
    }
    .introInfo {
        margin: 2rem;
    }
    .name {
        margin: 1rem 0;
        font-size: 20px;
    }
    .author, .series {
        font-size: 14px;
        color: #363636;
    }
    .tags {
        display: flex;
    }
    .type, .lang, .pages {
        padding: 7px 10px;
        margin-top: 2rem;
        margin-right: 1rem;
        background-color: #000;
        color: #fff;
        border-radius: 10px;
        width: fit-content;
        font-size: 15px;
    }
    .summary {
        margin-top: 2rem;
        padding: 0.5rem;
    }
    .summary h2 {
        font-size: 17px;
    }
    .summary p {
        font-size: 15px;
    }
    @media (max-width:700px) {
        .info {
            flex-direction: column;
        }
        .introInfo {
            margin: 2rem 0;
        }
        .tags {
            flex-wrap: wrap;
        }
        .type, .lang, .pages {
            margin-top: 0.5rem;
        }
    }
</style>