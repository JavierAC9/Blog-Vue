<template>
    <div class="general">
    <div class="center">
	<section id="content">
                <h1 class="subheader">Películas</h1>

                <div class="mis-datos" v-if="misDatos">
                    <p v-html="misDatos"></p>
                    <br>
                    {{web | mayusculas | concatenaYear('Este no ha sido el mejor año')}}
                </div>

                <div class="favorita" v-if="favorita">
                    <h3>La película marcada es</h3>
                    <h4>{{favorita.title}}</h4>
                </div>
                
                <!--Listado articulos-->
                <div id="articles">
                   <div v-for="pelicula in peliculasMayuscula" v-bind:key="pelicula.title">
                        <Pelicula :pelicula = "pelicula" @favorita="haLlegadoLaPeliculaFavorita"></Pelicula>
                   </div>
                </div>
                
            </section>
 <Sidebar></Sidebar>
        <div class="clearfix"></div>
    </div>
</div>
</template>


<script>
    import Pelicula from './Pelicula.vue';
    import Sidebar from './Sidebar.vue';

	export default {
		name: 'Peliculas',
        components: {
            Pelicula,
            Sidebar
        },
        methods: {
            haLlegadoLaPeliculaFavorita(favorita){
              this.favorita = favorita;
            }
        },
        filters: {
            mayusculas(value){
                return value.toUpperCase();
            },
            concatenaYear(value, message){
                var date = new Date();
                return value + ' ' + date.getFullYear() + ' ' + message;
            }
        }
        ,
        computed: {
            peliculasMayuscula(){
                var peliculasMod = this.peliculas;
                for(var i = 0; i < this.peliculas.length; i++){
                    peliculasMod[i].title = peliculasMod[i].title.toUpperCase(); 
                }
                return peliculasMod;
            },
            misDatos(){
                return this.nombre + '' + this.apellidos + '<br>' + '<strong>Sitio web:</strong> ' + this.web;
            }
        }   
        ,
        data(){
            return{
                nombre: 'Javier',
                apellidos: 'Álvarez Chavarría',
                web: 'javierac.com',
                favorita: null,
                peliculas: [
                    {title: 'Batman vs Superman', year: 2017, image: "https://img2.rtve.es/im/3535960/?w=900"},
                    {title: 'Parasite', year: 2019, image: "https://i.ytimg.com/vi/isOGD_7hNIY/maxresdefault.jpg"},
                    {title: 'Interstellar', year: 2014, image: "https://www.cinemascomics.com/wp-content/uploads/2020/08/Interstellar-secuela-960x720.jpg"}
                ]
            }
        }
	};
</script>