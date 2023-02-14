<template>
    <div class="cards-galery">
      <div class="heaven">
        <h1>La Divina Buenaventura</h1>
        <p class="sub-h">...mezcla y escoje una carta para saber que te depara la divina buenaventura...</p>
        <button type="button" class="shakebutton" v-on:click="shakeCards(),mixCards(images),listCards()">
        mezclar las cartas
        </button>
      </div>
      <div class="slider-cards">
            <div class="initial-position-cards" v-for="image in images" :key="image.id">
            <a href="#" v-on:click="showImage(image),scrollToCard()"><img class="image-fluid-card card" v-bind:src="image.backcard" alt=""/></a>
            </div>
      </div>
      <div>
        <div class="showed-card">
          <div v-if="selectedImage" id="showed-card" class="">
                <img class="card" :src="selectedImage.carta" alt="" srcset="" />
                <h2>{{ selectedImage.nombre }}</h2>
                <p>{{ selectedImage.significado }}</p>
          </div>
        </div>
        <button type="button" class="shakebutton" v-on:click="reload()">
          volver a tirar
        </button>
      </div>
          <div class="button-reload">

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
            "El Emperador es la contraparte de la Emperatriz y simboliza una influencia poderosa, generalmente de naturaleza masculina. Esto también puede incluir conceptos en tu vida que han sido considerados históricamente masculinos, como el liderazgo y autoridad, autodisciplina y la estabilidad a través del poder de la acción. Sus influencias positivas sugieren que puedes estar en el camino de una promoción o avance, pero también puede ser neutral. Usualmente es el compañero de aquellos destinados a asumir una mayor responsabilidad, puede presagiar cambios o pérdidas que requieren que des un paso adelante para asumir una mayor carga a la que ya tenías en el pasado. Cualquiera sea el ímpetu del cambio, indica que puedes poseer una fuerza interior fuera de lo común que te obligará a actuar y liderar.",
        },
        {
          id: 5,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/5-ElSumoSacerdote.jpg"),
          nombre: "El Sumo Sacerdote",
          significado:
            "Dependiendo de tu propia naturaleza, el Hierofante puede significar cosas muy diferentes. Básicamente representa la doctrina, pero la doctrina puede venir en manera de enseñanza y guía o de una autoridad rígida. En qué parte de tu tirada aparece también es importante dado que a menudo indica tu propia perspectiva de las convenciones morales, religiosas y sociales del mundo. Si se lo considera sabiamente, ayuda a mostrarnos el camino hacia la realización.",
        },
        {
          id: 6,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/6-LosEnamorados.jpg"),
          nombre: "Los Enamorados",
          significado:
            "Tu primer instinto será asociar esta carta como representante del amor, pero al igual que el amor ésta no posee una naturaleza simple. El amor no solo viene en formas diversas sino que los Amantes pueden indicar que se avecinan decisiones difíciles o importantes en tu vida. Esto es malo en el sentido de que estas decisiones son por lo general mutuamente excluyentes, son caminos a dos futuros totalmente diferentes. Pero también es Buena ya que confirma que al menos uno de esos caminos te llevará al lugar correcto. Por lo tanto, si encuentras esta carta en tu tirada debes de tomarla en cuenta con cautela pero sin miedo. Ella dice que se vienen decisiones difíciles, incluso dolorosas, pero que la decisión correcta que traerá un resultado positivo está al alcance de tu mano.",
        },
        {
          id: 7,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/7-ElCarro.jpg"),
          nombre: "El Carro",
          significado:
            "Tienes trabajo arduo frente a ti. Se puede resolver rápidamente, pero El Carro es una carta fuerte y la labor a la que te estás comprometiendo probablemente sea larga y difícil. Es muy posible que experimentes caminos duros, largos, largas pendientes ascendentes, callejones sin salida y reveses dolorosos. Un buen resultado sólo puede ser asegurado si la carta está de pie. Pero no pierdas la esperanza. Este duro camino te inspirará un fuerte sentido de propósito, la habilidad de triunfar a través de organización y Resistencia, y la confianza que solo poseen aquellos que han hecho algo que no creían posible. Aprovechado correctamente, pocas fuerzas pueden enfrentarse contra una persona así.",
        },
        {
          id: 8,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/8-LaJusticia.jpg"),
          nombre: "La Justicia",
          significado:
            "Es muy bueno encontrar la carta de la Justicia en tu tirada si has actuado con bondad y equidad respecto a los demás, especialmente si has sido una víctima. Es un indicador importante de una resolución positiva, aunque cómo y de qué clase dependerá de tus propias experiencias. Sin embargo, si has sido injusto, abusivo e inmoral en tus tratos entonces presta atención. En el mejor de los casos, esta carta representa para los injustos una advertencia para que cambien su forma de ser antes de que les caiga un castigo, y en el peor de los casos es un mensaje de que ya es demasiado tarde. En casos neutros puede simplemente estar diciéndote que busques el equilibro en tu vida.",
        },
        {
          id: 9,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/9-ElErmitaño.jpg"),
          nombre: "El Ermitaño",
          significado:
            "Hay momentos en la vida en que uno debe dar un paso atrás y examinar cuidadosamente las situaciones y decisiones que toma. El encontrar al Ermitaño en tu turada sugiere que este momento ha llegado para ti. Necesitas de un periodo de reflexión interior, lejos de las actuales demandas de tu posición. Este retiro puede ser físico o una búsqueda interior. Sólo una introspección honesta y profunda te llevará a una solución.",
        },
        {
          id: 10,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/10-LaRuedadelaFortuna.jpg"),
          nombre: "La Rueda de la Fortuna",
          significado:
            "La Rueda de la Fortuna simboliza los ciclos de la vida y habla de nuevos inicios. Es muy probable que encuentres que estos eventos sean positivos, pero al ser regidos por la suerte, puede que estén fuera de tu control e influencia. Atiende a aquellas cosas que puedes controlar con cuidado, y aprende a no sufrir con aquellos que no puedes controlar.",
        },
        {
          id: 11,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/11-LaFuerza.jpg"),
          nombre: "La Fuerza",
          significado:
            "La Fuerza es la forma más básica de poder y tú la posees de alguna manera. Esta es una carta muy feliz si te encuentras luchando contra una enfermedad o recuperándote de alguna lesión. Como he de sospecharse, su influencia sobre ti y el uso que le des puede orientarse hacia la luz o la oscuridad. Es probable que tiendas a enfrentarte a tus problemas con valentía y los conquistes a través de perseverancia y voluntad. Con esta habilidad de superar los obstáculos de la vida viene también la responsabilidad de controlarte a ti mismo. Esta carta puede ser una alerta para tomar las riendas de tus propias acciones y emociones antes de que te dañen a ti o a las personas que te importan.",
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
            "La Muerte indica cambios en tu futuro. Este cambio se puede dar en casi cualquier aspecto de tu vida, pero de seguro será permanente, significativo y absoluto. La Muerte sugiere una completa separación entre el pasado y el futuro y será muy probablemente dolorosa. A pesar de la sensación de pérdida que la pueda acompañar, La Muerte cumple un rol natural e importante de la vida, y nos lleva eventualmente a la aceptación. Es una parte necesaria para seguir avanzando y verás que los cambios son más sencillos si los aceptas en vez de luchar en su contra. Espera el fin de una amistad cercana, un trabajo, un matrimonio o incluso de la vida, pero no te enfoques demasiado en lo negativo.",
        },
        {
          id: 14,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/14-LaTemplanza.jpg"),
          nombre: "La Templanza",
          significado:
            "La Templanza es una carta optimista que te anima a encontrar un equilibrio en tu vida y abordar los problemas con una actitud calmada. Ella reconoce que las fuerzas opuestas no necesitan estar en guerra dentro de ti. Pisa con cuidado en todas las decisiones importantes que tomes. Confía en que las buenas decisiones llevarán a un resultado positive para ti.",
        },
        {
          id: 15,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/15-ElDiablo.jpg"),
          nombre: "El Diablo",
          significado:
            "El Diablo está en el negocio de la trampa. Señala que hay una situación de la cual no hay escapatoria, o un camino que conduce a ésta. El aviso puede permitirte evitar la trampa, o tal vez no. El tipo de trampa y cómo debes de evitarla dependerá del lugar que el Diablo ocupe en tu tirada y de las cartas que lo rodean. Esta carta no predice la condenación, solo la necesidad de prudencia.",
        },
        {
          id: 16,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/16-LaTorre.jpg"),
          nombre: "La Torre",
          significado:
            "Oscura y amenazante, la Torre es la encarnación de la complicación y el conflicto. No solo el cambio, sino el movimiento brusco y desagradable causado por los acontecimientos imprevistos y traumáticos que forman parte de la vida. La Torre en tu tirada siempre es una amenaza, pero la vida inevitablemente implica tragedia, y debes de decidir si la enfrentarás con gracia.",
        },
        {
          id: 17,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/17-LaEstrella.jpg"),
          nombre: "La Estrella",
          significado:
            "La presencia de la Estrella significa un periodo de descanso y renovación para ti. Esta renovación puede ser spiritual, física o ambas. Es un signo particularmente positivo de que tú o alguien cercano a ti se están recuperando de una enfermedad o lesión. Es una luz en la oscuridad iluminando tu futuro y tu pasado.",
        },
        {
          id: 18,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/18-LaLuna.jpg"),
          nombre: "La Luna",
          significado:
            "Algo en tu vida no es lo que parece. Tal vez hay algo que no has comprendido bien o hay una verdad que te rehúsas a aceptar. También puede significar que hay algo importante que se te está siendo ocultado por otra persona. Esto puede causar preocupación y depresión en tu vida y la Luna es un fuerte indicador de que debes de apoyarte en tu intuición para ver a través del subterfugio.",
        },
        {
          id: 19,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/19-ElSol.jpg"),
          nombre: "El Sol",
          significado:
            "El sol representa un desarrollo positivo y tiene una Buena influencia inherente. Sugiere ganancia personal y alegría, y que las metas personales están al alcance de tus manos si estás dispuesto a esforzarte por ellas. Si estás embarcándote en un nuevo emprendimiento personal, como el matrimonio o empezar una familia, el Sol es de particular influencia.",
        },
        {
          id: 20,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/20-ElJuicio.jpg"),
          nombre: "El Juicio",
          significado:
            "El Juicio habla sobre una transición, pero a diferencia de la Muerte o la Torre, el cambio no es súbito, ni procede de la suerte o la intuición, sino que es un cambio que proviene de la razón. Significa que los planes, que con frecuencia han tardado tiempo en llevarse a cabo, van a rendir frutos, Si apunta hacia el futuro, también puede hablar de la naturaleza del cambio. Si se necesita tomar una decisión, debes de dejar que tu mente la tome. En este caso, la lógica es mejor guía que la intuición. Debes estar preparado para tomar una gran decisión en tu vida, probablemente una que dará forma al siguiente capítulo de tu vida.",
        },
        {
          id: 21,
          backcard: require("@/assets/cards/Fondo.jpg"),
          carta: require("@/assets/cards/21-ElMundo.jpg"),
          nombre: "El Mundo",
          significado:
            "El Mundo es un indicador de un cambio importante e inexorable, de amplitud tectónica. Este cambio representa una oportunidad para tu para terminar con lo Viejo y darle un buen inicio a lo Nuevo. Esta carta indica un crecimiento en la madurez, un sentido de equilibrio interno y un entendimiento más profundo. Sugiere que puedes estar aproximándote a una compresión más madura de tu identidad y la seguridad en ti mismo que viene con la edad. También representa la caída de las barreras, a veces de sentido espiritual, pero a veces en el sentido puramente físico, indicando un futuro con viajes.",
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
        return image;
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
        },6000)
    },

    scrollToCard: function(){
        setTimeout(()=>{
          window.scroll({
              top: 700,
              left: 0,
              behavior: 'smooth'
          });
          
        },100)
        

    },

    reload: function(){
        location.reload();
        window.scrollTo(0, 0);
    }

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
  width: 85%;
  display: flex;
  margin: 500px auto 10px auto;
  border-bottom: 2px solid #d7be8a;
  padding-bottom: 50px;
}

.button-reload{
  margin: 0 auto;
}
</style>