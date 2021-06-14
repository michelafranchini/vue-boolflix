<template>
    <div class="film">
        <ul>
            <li>{{item.title}}</li>
            <li>{{item.original_title}}</li>
            <li>{{item.original_language}}</li>

        </ul>
    </div>
</template>

<script>

export default {
    name: "Film", 
    props: ["item"]
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

    .film {
        @include starSettings;
        background-color: yellow;
        width: 200px;
        height: 200px;
    }
</style>