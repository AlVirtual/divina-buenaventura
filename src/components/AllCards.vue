<template>
    <div class="cards-galery">
      <div class="heaven">
        <h1>La Divina Buenaventura</h1>
        <button type="button" class="shakebutton" v-on:click="shakeCards(),mixCards(images),listCards()">
        mezcla las cartas
        </button>
      </div>
      <div class="slider-cards">
            <div class="initial-position-cards" v-for="image in images" :key="image.id">
            <a href="#" v-on:click="showImage(image)"><img class="image-fluid-card card" v-bind:src="image.backcard" alt=""/></a>
            </div>
      </div>

      <div class="showed-card">
          <div class="">
                <img class="card" :src="selectedImage.carta" alt="" srcset="" />
                <h2>{{ selectedImage.nombre }}</h2>
                <p>{{ selectedImage.significado }}</p>
          </div>
      </div>
    </div>
  
</template>

<script>
export default {
    name: 'AllCards',
  data() {
    return {
      backcard: require("@/assets/cards/Fondo.jpg"),
      selectedImage: "",
      images: [
        {
          id: 0,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/0-ElLoco.jpg"),
          nombre: "El Loco",
          significado:
            "El Loco es una carta muy poderosa de la baraja del Tarot que usualmente representa un nuevo comienzo y como consecuencia el fin de algo en tu vida anterior. La posición del Loco en tu tirada revela qué aspectos de tu vida pueden estar sujetos a cambios. El Loco anuncia que se vienen importantes decisiones que pueden ser difíciles de tomar, y que pueden significar un riesgo para ti. Acércate a los cambios con optimismo y cuidado para obtener el resultado más positivo posible.",
        },
        {
          id: 1,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/1-ElMago.jpg"),
          nombre: "El Mago",
          significado:
            "El Mago generalmente se asocial con los comunicadores inteligentes y hábiles. Su presencia en tu tirada indica que posees un nivel de autoconfianza y determinación que te permiten traducir las ideas en acciones. Ésta es una carta muy práctica cuyas revelaciones son mejor aplicadas a los aspectos pragmáticos y físicos de tu vida, mas no en los teóricos o efímeros. Tu éxito en emprendimientos futuros en la política o los negocios dependerán de tu propia fuerza de voluntad y determinación.",
        },
        {
          id: 2,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/2-LaSacerdotisa.jpg"),
          nombre: "La Sacerdotisa",
          significado:
            "Tu asociación con la Sacerdotisa sugiere que posees buen juicio en la forma de una fuerte intuición. Ella puede estar indicando que la razón debe pasar a segundo plano frente al instinto. Tu cabeza debe confiar en la sabiduría de tu corazón. Sin embargo, ella también simboliza la ayuda de la naturaleza y su presencia en ciertas partes de tu tirada puede indicar que alguien cercano a ti va a venir en tu rescate con su intuición. La intuición también es más efectiva para ver aquello que está oculto a los sentidos. Por lo tanto, la Sacerdotisa puede también simbolizar una advertencia de hechos ocultos que son o serán importantes para ti.",
        },
        {
          id: 3,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/3-LaEmperatriz.jpg"),
          nombre: "La Emperatriz",
          significado:
            "Tradicionalmente se le ha asociado con una fuerte influencia maternal, la presencia de la Emperatriz te trae excelentes noticias si estás buscando la armonía en tu matrimonio o esperar iniciar una familia. Cualquier actividad artística en la que estés actualmente envuelto será más exitosa ya que esta carta con frecuencia encuentra a aquellos que están expuestos a fuertes ráfagas de energía creativa o artística. Sin embargo, esa energía creativa puede no estar en la forma de una pintura o un proyecto artístico. Esta carta también sugiere una fuerte posibilidad de embarazo -- no necesariamente tuya, pero podrías ver una nueva adición a tu familia o la familia de un amigo cercano en el futuro cercano. Esta carta es de buen augurio para ti y quienes te rodean.",
        },
        {
          id: 4,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/4-ElEmperador.jpg"),
          nombre: "El Emperador",
          significado:
            "Tradicionalmente se le ha asociado con una fuerte influencia maternal, la presencia de la Emperatriz te trae excelentes noticias si estás buscando la armonía en tu matrimonio o esperar iniciar una familia. Cualquier actividad artística en la que estés actualmente envuelto será más exitosa ya que esta carta con frecuencia encuentra a aquellos que están expuestos a fuertes ráfagas de energía creativa o artística. Sin embargo, esa energía creativa puede no estar en la forma de una pintura o un proyecto artístico. Esta carta también sugiere una fuerte posibilidad de embarazo -- no necesariamente tuya, pero podrías ver una nueva adición a tu familia o la familia de un amigo cercano en el futuro cercano. Esta carta es de buen augurio para ti y quienes te rodean.",
        },
        {
          id: 5,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/5-ElSumoSacerdote.jpg"),
          nombre: "El Sumo Sacerdote",
          significado:
            "Tradicionalmente se le ha asociado con una fuerte influencia maternal, la presencia de la Emperatriz te trae excelentes noticias si estás buscando la armonía en tu matrimonio o esperar iniciar una familia. Cualquier actividad artística en la que estés actualmente envuelto será más exitosa ya que esta carta con frecuencia encuentra a aquellos que están expuestos a fuertes ráfagas de energía creativa o artística. Sin embargo, esa energía creativa puede no estar en la forma de una pintura o un proyecto artístico. Esta carta también sugiere una fuerte posibilidad de embarazo -- no necesariamente tuya, pero podrías ver una nueva adición a tu familia o la familia de un amigo cercano en el futuro cercano. Esta carta es de buen augurio para ti y quienes te rodean.",
        },
        {
          id: 6,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/6-LosEnamorados.jpg"),
          nombre: "Los Enamorados",
          significado:
            "Tradicionalmente se le ha asociado con una fuerte influencia maternal, la presencia de la Emperatriz te trae excelentes noticias si estás buscando la armonía en tu matrimonio o esperar iniciar una familia. Cualquier actividad artística en la que estés actualmente envuelto será más exitosa ya que esta carta con frecuencia encuentra a aquellos que están expuestos a fuertes ráfagas de energía creativa o artística. Sin embargo, esa energía creativa puede no estar en la forma de una pintura o un proyecto artístico. Esta carta también sugiere una fuerte posibilidad de embarazo -- no necesariamente tuya, pero podrías ver una nueva adición a tu familia o la familia de un amigo cercano en el futuro cercano. Esta carta es de buen augurio para ti y quienes te rodean.",
        },
        {
          id: 7,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/7-ElCarro.jpg"),
          nombre: "El Carro",
          significado:
            "Tradicionalmente se le ha asociado con una fuerte influencia maternal, la presencia de la Emperatriz te trae excelentes noticias si estás buscando la armonía en tu matrimonio o esperar iniciar una familia. Cualquier actividad artística en la que estés actualmente envuelto será más exitosa ya que esta carta con frecuencia encuentra a aquellos que están expuestos a fuertes ráfagas de energía creativa o artística. Sin embargo, esa energía creativa puede no estar en la forma de una pintura o un proyecto artístico. Esta carta también sugiere una fuerte posibilidad de embarazo -- no necesariamente tuya, pero podrías ver una nueva adición a tu familia o la familia de un amigo cercano en el futuro cercano. Esta carta es de buen augurio para ti y quienes te rodean.",
        },
        {
          id: 8,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/8-LaJusticia.jpg"),
          nombre: "La Justicia",
          significado:
            "El Loco es una carta muy poderosa de la baraja del Tarot que usualmente representa un nuevo comienzo y como consecuencia el fin de algo en tu vida anterior. La posición del Loco en tu tirada revela qué aspectos de tu vida pueden estar sujetos a cambios. El Loco anuncia que se vienen importantes decisiones que pueden ser difíciles de tomar, y que pueden significar un riesgo para ti. Acércate a los cambios con optimismo y cuidado para obtener el resultado más positivo posible.",
        },
        {
          id: 9,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/9-ElErmitaño.jpg"),
          nombre: "El Ermitaño",
          significado:
            "El Mago generalmente se asocial con los comunicadores inteligentes y hábiles. Su presencia en tu tirada indica que posees un nivel de autoconfianza y determinación que te permiten traducir las ideas en acciones. Ésta es una carta muy práctica cuyas revelaciones son mejor aplicadas a los aspectos pragmáticos y físicos de tu vida, mas no en los teóricos o efímeros. Tu éxito en emprendimientos futuros en la política o los negocios dependerán de tu propia fuerza de voluntad y determinación.",
        },
        {
          id: 10,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/10-LaRuedadelaFortuna.jpg"),
          nombre: "La Rueda de la Fortuna",
          significado:
            "Tu asociación con la Sacerdotisa sugiere que posees buen juicio en la forma de una fuerte intuición. Ella puede estar indicando que la razón debe pasar a segundo plano frente al instinto. Tu cabeza debe confiar en la sabiduría de tu corazón. Sin embargo, ella también simboliza la ayuda de la naturaleza y su presencia en ciertas partes de tu tirada puede indicar que alguien cercano a ti va a venir en tu rescate con su intuición. La intuición también es más efectiva para ver aquello que está oculto a los sentidos. Por lo tanto, la Sacerdotisa puede también simbolizar una advertencia de hechos ocultos que son o serán importantes para ti.",
        },
        {
          id: 11,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/11-LaFuerza.jpg"),
          nombre: "La Fuerza",
          significado:
            "Tradicionalmente se le ha asociado con una fuerte influencia maternal, la presencia de la Emperatriz te trae excelentes noticias si estás buscando la armonía en tu matrimonio o esperar iniciar una familia. Cualquier actividad artística en la que estés actualmente envuelto será más exitosa ya que esta carta con frecuencia encuentra a aquellos que están expuestos a fuertes ráfagas de energía creativa o artística. Sin embargo, esa energía creativa puede no estar en la forma de una pintura o un proyecto artístico. Esta carta también sugiere una fuerte posibilidad de embarazo -- no necesariamente tuya, pero podrías ver una nueva adición a tu familia o la familia de un amigo cercano en el futuro cercano. Esta carta es de buen augurio para ti y quienes te rodean.",
        },
        {
          id: 12,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/12-ElColgado.jpg"),
          nombre: "El Colgado",
          significado:
            "Tradicionalmente se le ha asociado con una fuerte influencia maternal, la presencia de la Emperatriz te trae excelentes noticias si estás buscando la armonía en tu matrimonio o esperar iniciar una familia. Cualquier actividad artística en la que estés actualmente envuelto será más exitosa ya que esta carta con frecuencia encuentra a aquellos que están expuestos a fuertes ráfagas de energía creativa o artística. Sin embargo, esa energía creativa puede no estar en la forma de una pintura o un proyecto artístico. Esta carta también sugiere una fuerte posibilidad de embarazo -- no necesariamente tuya, pero podrías ver una nueva adición a tu familia o la familia de un amigo cercano en el futuro cercano. Esta carta es de buen augurio para ti y quienes te rodean.",
        },
        {
          id: 13,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/13-LaMuerte.jpg"),
          nombre: "El Arcano sin Nobre",
          significado:
            "Tradicionalmente se le ha asociado con una fuerte influencia maternal, la presencia de la Emperatriz te trae excelentes noticias si estás buscando la armonía en tu matrimonio o esperar iniciar una familia. Cualquier actividad artística en la que estés actualmente envuelto será más exitosa ya que esta carta con frecuencia encuentra a aquellos que están expuestos a fuertes ráfagas de energía creativa o artística. Sin embargo, esa energía creativa puede no estar en la forma de una pintura o un proyecto artístico. Esta carta también sugiere una fuerte posibilidad de embarazo -- no necesariamente tuya, pero podrías ver una nueva adición a tu familia o la familia de un amigo cercano en el futuro cercano. Esta carta es de buen augurio para ti y quienes te rodean.",
        },
        {
          id: 14,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/14-LaTemplanza.jpg"),
          nombre: "La Templanza",
          significado:
            "Tradicionalmente se le ha asociado con una fuerte influencia maternal, la presencia de la Emperatriz te trae excelentes noticias si estás buscando la armonía en tu matrimonio o esperar iniciar una familia. Cualquier actividad artística en la que estés actualmente envuelto será más exitosa ya que esta carta con frecuencia encuentra a aquellos que están expuestos a fuertes ráfagas de energía creativa o artística. Sin embargo, esa energía creativa puede no estar en la forma de una pintura o un proyecto artístico. Esta carta también sugiere una fuerte posibilidad de embarazo -- no necesariamente tuya, pero podrías ver una nueva adición a tu familia o la familia de un amigo cercano en el futuro cercano. Esta carta es de buen augurio para ti y quienes te rodean.",
        },
        {
          id: 15,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/15-ElDiablo.jpg"),
          nombre: "El Diablo",
          significado:
            "Tradicionalmente se le ha asociado con una fuerte influencia maternal, la presencia de la Emperatriz te trae excelentes noticias si estás buscando la armonía en tu matrimonio o esperar iniciar una familia. Cualquier actividad artística en la que estés actualmente envuelto será más exitosa ya que esta carta con frecuencia encuentra a aquellos que están expuestos a fuertes ráfagas de energía creativa o artística. Sin embargo, esa energía creativa puede no estar en la forma de una pintura o un proyecto artístico. Esta carta también sugiere una fuerte posibilidad de embarazo -- no necesariamente tuya, pero podrías ver una nueva adición a tu familia o la familia de un amigo cercano en el futuro cercano. Esta carta es de buen augurio para ti y quienes te rodean.",
        },
        {
          id: 16,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/16-LaTorre.jpg"),
          nombre: "La Tore",
          significado:
            "Tu asociación con la Sacerdotisa sugiere que posees buen juicio en la forma de una fuerte intuición. Ella puede estar indicando que la razón debe pasar a segundo plano frente al instinto. Tu cabeza debe confiar en la sabiduría de tu corazón. Sin embargo, ella también simboliza la ayuda de la naturaleza y su presencia en ciertas partes de tu tirada puede indicar que alguien cercano a ti va a venir en tu rescate con su intuición. La intuición también es más efectiva para ver aquello que está oculto a los sentidos. Por lo tanto, la Sacerdotisa puede también simbolizar una advertencia de hechos ocultos que son o serán importantes para ti.",
        },
        {
          id: 17,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/17-LaEstrella.jpg"),
          nombre: "La Estrella",
          significado:
            "Tradicionalmente se le ha asociado con una fuerte influencia maternal, la presencia de la Emperatriz te trae excelentes noticias si estás buscando la armonía en tu matrimonio o esperar iniciar una familia. Cualquier actividad artística en la que estés actualmente envuelto será más exitosa ya que esta carta con frecuencia encuentra a aquellos que están expuestos a fuertes ráfagas de energía creativa o artística. Sin embargo, esa energía creativa puede no estar en la forma de una pintura o un proyecto artístico. Esta carta también sugiere una fuerte posibilidad de embarazo -- no necesariamente tuya, pero podrías ver una nueva adición a tu familia o la familia de un amigo cercano en el futuro cercano. Esta carta es de buen augurio para ti y quienes te rodean.",
        },
        {
          id: 18,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/18-LaLuna.jpg"),
          nombre: "La Luna",
          significado:
            "Tradicionalmente se le ha asociado con una fuerte influencia maternal, la presencia de la Emperatriz te trae excelentes noticias si estás buscando la armonía en tu matrimonio o esperar iniciar una familia. Cualquier actividad artística en la que estés actualmente envuelto será más exitosa ya que esta carta con frecuencia encuentra a aquellos que están expuestos a fuertes ráfagas de energía creativa o artística. Sin embargo, esa energía creativa puede no estar en la forma de una pintura o un proyecto artístico. Esta carta también sugiere una fuerte posibilidad de embarazo -- no necesariamente tuya, pero podrías ver una nueva adición a tu familia o la familia de un amigo cercano en el futuro cercano. Esta carta es de buen augurio para ti y quienes te rodean.",
        },
        {
          id: 19,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/19-ElSol.jpg"),
          nombre: "El Sol",
          significado:
            "Tradicionalmente se le ha asociado con una fuerte influencia maternal, la presencia de la Emperatriz te trae excelentes noticias si estás buscando la armonía en tu matrimonio o esperar iniciar una familia. Cualquier actividad artística en la que estés actualmente envuelto será más exitosa ya que esta carta con frecuencia encuentra a aquellos que están expuestos a fuertes ráfagas de energía creativa o artística. Sin embargo, esa energía creativa puede no estar en la forma de una pintura o un proyecto artístico. Esta carta también sugiere una fuerte posibilidad de embarazo -- no necesariamente tuya, pero podrías ver una nueva adición a tu familia o la familia de un amigo cercano en el futuro cercano. Esta carta es de buen augurio para ti y quienes te rodean.",
        },
        {
          id: 20,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/20-ElJuicio.jpg"),
          nombre: "El Juicio",
          significado:
            "Tradicionalmente se le ha asociado con una fuerte influencia maternal, la presencia de la Emperatriz te trae excelentes noticias si estás buscando la armonía en tu matrimonio o esperar iniciar una familia. Cualquier actividad artística en la que estés actualmente envuelto será más exitosa ya que esta carta con frecuencia encuentra a aquellos que están expuestos a fuertes ráfagas de energía creativa o artística. Sin embargo, esa energía creativa puede no estar en la forma de una pintura o un proyecto artístico. Esta carta también sugiere una fuerte posibilidad de embarazo -- no necesariamente tuya, pero podrías ver una nueva adición a tu familia o la familia de un amigo cercano en el futuro cercano. Esta carta es de buen augurio para ti y quienes te rodean.",
        },
        {
          id: 21,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/21-ElMundo.jpg"),
          nombre: "El Mundo",
          significado:
            "Tradicionalmente se le ha asociado con una fuerte influencia maternal, la presencia de la Emperatriz te trae excelentes noticias si estás buscando la armonía en tu matrimonio o esperar iniciar una familia. Cualquier actividad artística en la que estés actualmente envuelto será más exitosa ya que esta carta con frecuencia encuentra a aquellos que están expuestos a fuertes ráfagas de energía creativa o artística. Sin embargo, esa energía creativa puede no estar en la forma de una pintura o un proyecto artístico. Esta carta también sugiere una fuerte posibilidad de embarazo -- no necesariamente tuya, pero podrías ver una nueva adición a tu familia o la familia de un amigo cercano en el futuro cercano. Esta carta es de buen augurio para ti y quienes te rodean.",
        },
      ],
    };
  },
  methods: {

    shakeCards: function () {
        const shakeclases = document.querySelectorAll(".initial-position-cards");
        for (let i = 0; i < shakeclases.length; i++) {
        shakeclases[i].classList.toggle("shake" + [i]);
        }
        setTimeout(()=>{
        for (let i = 0; i < shakeclases.length; i++) {
        shakeclases[i].classList.toggle("shake" + [i]);
        }
        },5000)
        
    },

    showImage: function (image) {
        this.selectedImage = image;
    },
    
    mixCards: function (images) {
        setTimeout(()=>{
            this.images = images.sort(function () {
                return Math.random() - 0.5;
            });

        },6000)

    },
    
    listCards: function () {
        setTimeout(()=>{
            const listclases = document.querySelectorAll(".initial-position-cards");
            console.log(listclases);
            for (let i = 0; i < listclases.length; i++) {
                listclases[i].classList.toggle("initial-position-cards");
                listclases[i].classList.toggle("list" + [i]);
            }
        },7000)
    },
  },
};
</script>

<style scoped>

.initial-position-cards {
  margin-left: auto;
  margin-right: auto;
  left: 0;
  right: 0;
  position: absolute;
}

.shake-cards {
  margin-bottom: 100px;
}

.image-fluid-card:hover {
  margin-top: -20px;
}

.slider-cards {
  width: 80%;
  margin: 10px auto 10px auto;
  display: flex;
}


.shakebutton{
  margin-top: 10px;
  margin-bottom: 20px;
}


.shake1 {
  animation: moveone 1.5s ease;
  animation-iteration-count: 3;
}
@keyframes moveone {
  50%{
    transform: translate(290px);
  }
}

.shake2 {
  animation: movetwo 1s ease;
  animation-iteration-count: 3;
}
@keyframes movetwo {
  50% {
    transform: translate(290px);
  }
}

.shake3 {
  animation: movethree 2s ease;
  animation-iteration-count: 2;
}
@keyframes movethree {
  50% {
    transform: translate(-290px);
  }
}

.list0 {
    position: absolute;
    display: inline;
    left: 10%;
}

.list1{
    position: absolute;
    display: inline;
    left: 13%;
}

.list2{
    position: absolute;
    display: inline;
    left: 16%;
}

.list3{
    position: absolute;
    display: inline;
    left: 19%;
}

.list4{
    position: absolute;
    display: inline;
    left: 22%;
}

.list5{
    position: absolute;
    display: inline;
    left: 25%;
}

.list6{
    position: absolute;
    display: inline;
    left: 28%;
}

.list7{
    position: absolute;
    display: inline;
    left: 31%;
}

.list8{
    position: absolute;
    display: inline;
    left: 34%;
}

.list9{
    position: absolute;
    display: inline;
    left: 37%;
}

.list10{
    position: absolute;
    display: inline;
    left: 40%;
}

.list11{
    position: absolute;
    display: inline;
    left: 43%;
}

.list12{
    position: absolute;
    display: inline;
    left: 46%;
}

.list13{
    position: absolute;
    display: inline;
    left: 49%;
}

.list14{
    position: absolute;
    display: inline;
    left: 52%;
}

.list15{
    position: absolute;
    display: inline;
    left: 55%;
}

.list16{
    position: absolute;
    display: inline;
    left: 58%;
}

.list17{
    position: absolute;
    display: inline;
    left: 61%;
}

.list18{
    position: absolute;
    display: inline;
    left: 64%;
}

.list19{
    position: absolute;
    display: inline;
    left: 67%;
}

.list20{
    position: absolute;
    display: inline;
    left: 70%;
}

.list21{
    position: absolute;
    display: inline;
    left: 73%;
} 

.showed-card{
  width: 80%;
  display: flex;
  margin: 500px auto;
  border-bottom: 2px solid #d7be8a;
  padding-bottom: 50px;
}


</style>