<template>

    <section id="articles-component">

    <div id="articles-list" v-if="articles && articles.length >= 1">
     <article class="article-item" v-for="article in articles" :key="article._id" >
        <div class="image-wrap">
            <img :src="url + 'get-image/' + article.image" 
            :alt="article.title"
             v-if="article.image"/>
            <img src="https://images.vexels.com/media/users/3/128417/isolated/preview/d437da2a54918895cf59a3362a0099ec-album-de-fotos-plano-icono-by-vexels.png"
            :alt="article.title" 
            v-if="!article.image"/>
        </div>

        <h2>
            <router-link :to="{name: 'article', params: {id:article._id}}">
                {{article.title}}
            </router-link>
        </h2>

        <span class="date">
            {{article.date | moment('from','now')}}
        </span>
        <router-link :to="{name: 'article', params: {id:article._id}}">Leer más</router-link>

        <div class="clearfix"></div>
    </article>
    </div>

    <div v-else-if="articles && articles.length < 1">
        No hay artículos para mostrar
    </div>

    <div v-else>
        Cargando... 
    </div>

    </section>

</template>

<script>
    import Global from '../Global';

    export default{
        name: 'Articles',
        props: ['articles'],
        data(){
            return{
                url: Global.url
            }   
        }
    }
</script>