<template>
    <div class="general">
    <Slider texto="Página de pruebas"></Slider>
    <div class="center">
    <section id="content">
        <h2 class="subheader">Página de pruebas</h2>
        <h3>{{id_desde_url}}</h3>
        <h4>{{nombre}}</h4>
        <button @click="actualizarNombre()">Actualizar nombre</button>
        <button @click="redirigirBlog()">Redirigir al blog</button>
    </section>

 <Sidebar></Sidebar>
        <div class="clearfix"></div>
    </div>
</div>
</template>

<script>
    import Slider from './Slider.vue';
    import Sidebar from './Sidebar.vue';

    export default {
        name: 'Pagina',
        components: {
            Slider,
            Sidebar
        },
        created(){
            console.log('Componente CREADO!!!');
        },
        mounted(){
            this.id_desde_url = this.$route.params.id;
            console.log('Componente MONTADO!!!');
            console.log(this.nombre);
        },
        updated(){
            console.log('Componente ACTUALIZADO!!!');
        },
        destroyed(){
            console.log('Componente ELIMINADO!!!');
        },
        data(){
            return{
                id_desde_url: null,
                nombre: 'Javier Álvarez'
            };
        },
        methods: {
            actualizarNombre(){
            this.nombre = 'Javier Álvarez Chavarría'
            console.log(this.nombre);
        },
            redirigirBlog(){
                this.$router.push('/blog');
            }
        }
        
    };
</script>