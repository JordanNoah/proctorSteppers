<template>
  <v-app>
    <v-app-bar app color="primary" dark elevation="0">
      <v-container class="d-flex justify-space-between">
        <div>
          <h2>
            Sistema proctor
          </h2>
          <span>
            Nombre del examen
          </span>
        </div>
        <div class="d-flex align-end flex-column justify-center">
          <a href="#" class="white--text">Salir</a>
          <a href="#" class="white--text">Soporte Tecnico</a>
        </div>
      </v-container>
    </v-app-bar>
    <v-main>
      <v-container>
        <v-stepper v-model="mainStep" alt-labels flat>
          <v-stepper-header>
            <template v-for="(n, index) in steps">
              <v-stepper-step :complete="n.complete" :step="n.id" :key="n.id">
                <div style="text-align: center;">
                  {{ n.name }}
                </div>
              </v-stepper-step>
              <v-divider :key="index" v-if="n.id < steps.length "></v-divider>
            </template>
          </v-stepper-header>
          <v-stepper-items>
            <v-stepper-content step="1">
              <v-card class="mb-12" min-height="200px" elevation="0">
                <v-card-title>
                  Examen Supervisado
                </v-card-title>
                <v-card-text>
                  <p>
                    Con el fin de acreditar el cumplimiento de la normativa asociada a la realización de exámenes de
                    nuestra Universidad (especialmente, identificación de la persona que responde el examen, realización
                    individual de la prueba) se realiza la supervisión remota de exámenes a partir de un sistema de
                    grabación.
                  </p>
                  <p>
                    Requisitos:
                  </p>
                  <ul>
                    <li>
                      Cámara web (webcam)
                    </li>
                    <li>
                      Micrófono
                    </li>
                    <li>
                      PC de sobremesa
                    </li>
                    <li>
                      Teléfono con lector de códigos QR
                    </li>
                    <li>
                      Navegador actualizado (preferiblemente Chrome)
                    </li>
                    <li>
                      Acceso a internet
                    </li>
                    <li>
                      Documento acreditativo de la identidad
                    </li>
                  </ul>
                </v-card-text>
              </v-card>
              <v-btn class="mb-2 ml-1" @click="nextStep(1)">
                Continue
              </v-btn>
            </v-stepper-content>
            <v-stepper-content step="2" ref="stepperTwo">
              <v-card class="mb-12"  min-height="200px" elevation="0">
                <v-card-title>
                  Normas para realizar exámenes supervisados
                </v-card-title>
                <v-card-text>
                  <div ref="watchDefault">
                    <p>
                      Con el fin de acreditar el cumplimiento de la normativa asociada a la realización de exámenes de
                      nuestra Universidad (especialmente, identificación de la persona que responde el examen,
                      realización individual de la prueba) se realiza la supervisión remota de exámenes a partir de un
                      sistema de grabación.
                    </p>
                    <p>
                      Por este motivo, a continuación le detallamos el protocolo de actuación que deberá seguir cuando
                      realice un examen supervisado:
                    </p>
                    <ul>
                      <li>Acceda al examen desde un ordenador situado en un lugar tranquilo. Al tratarse de una prueba
                        individual, recuerde que deberá estar solo. Las grabaciones solo deben registrar la imagen de su
                        persona; evite que aparezcan otras personas en las grabaciones, tales como niños, compañeros de
                        trabajo, familiares, etc. De ser necesario, cierre la puerta de la habitación en la que se
                        encuentre e impida la entrada de otras personas. Para evitar interrupciones de otros, le
                        recomendamos, por ejemplo, que deje un aviso en la puerta de entrada al lugar donde se
                        encuentre.</li>
                      <li>Manténgase en silencio y evite cualquier ruido externo como, por ejemplo, música, radio o
                        televisión con el audio encendido, llamadas telefónicas, etc. Apague el teléfono antes de
                        iniciar el examen y silencie el altavoz de su ordenador para evitar ruidos molestos. Durante la
                        realización del examen, no está permitido comunicarse con ninguna persona ajena al equipo
                        supervisor.</li>
                      <li>Asegúrese de que las grabaciones registren en todo momento su rostro completo desde la
                        perspectiva frontal. Por lo tanto, evite espacios oscuros y el uso de gafas de sol o de
                        cualquier elemento que cubra su rostro e impida su correcta identificación; asimismo, evite
                        ladear el rostro y confirme, antes de empezar, que su rostro completo aparece en la imagen
                        registrada por su cámara web.</li>
                      <li>Antes de iniciar el examen, presente su documento identificativo y diga en voz alta su nombre.
                        Le recordamos que el micrófono debe estar activado para hacerlo. </li>
                      <li>Responda las preguntas del examen sin interrupciones. Recuerde que una vez iniciado el examen
                        dispondrá de un plazo para terminarlo y no podrá salir de él. Nada debe interrumpir que el
                        sistema remoto grabe su comportamiento durante la realización del examen, por lo que usted
                        deberá estar delante del ordenador sin ausentarse durante la prueba. </li>
                    </ul>
                    <p>En caso de no cumplir alguna de las consideraciones indicadas arriba se podrá anular el examen.
                    </p>
                    <p>La Universidad se compromete a no atentar contra la privacidad de ningún estudiante. El sistema
                      será utilizado única y exclusivamente como medio para la supervisión de exámenes.</p>
                  </div>
                  <div ref="watchMoreOne">
                    <v-card v-show="watchMoreOne">
                      <v-card-text>
                        <h5>¿Por qué se graban las entregas de trabajos y exámenes?</h5>
                        <p>La Universidad establece procesos con el fin de mejorar la calidad del programa que usted
                          está
                          cursando. En este
                          sentido se hace especial hincapié en aquellas acciones encaminadas a acreditar la fiabilidad
                          de
                          los procesos
                          académicos ante entidades oficiales de control y acreditación.</p>
                        <p>Por este motivo le animamos a que acepte el consentimiento para ayudarnos a acreditar la
                          veracidad de su
                          expediente académico ante estas agencias.</p>
                        <h5>¿Qué uso se da a estas grabaciones?</h5> El uso de las imágenes audiovisuales registradas
                        queda circusncrito
                        exclusivamente a los siguientes procesos de supervisión académica: <ul>
                          <li>procesos de acreditación ante entidades acreditadoras, como por ejemplo la ANECA, de los
                            procesos académicos
                            de nuestra organización;</li>
                          <li>procesos de validación de la autoría de los exámenes y trabajos;</li>
                          <li>procesos de certificación de ausencia de ayuda externa durante la realización de los
                            mismos.
                          </li>
                        </ul>
                        <h5>¿Quién va a acceder a estas grabaciones?</h5>
                        <p>Los destinatarios de la información serán el personal académico o administrativo de nuestra
                          organización que
                          tengan que supervisar los exámenes o trabajos realizados, así como el personal de las
                          entidades
                          acreditadoras
                          antes mencionadas siempre bajo el control de nuestra organización.</p>
                        <h5>¿Se van a ceder estas grabaciones a terceros?</h5>
                        <p>Nunca, estas grabaciones se almacenan en un sistema anonimizado y seguro, con control de
                          accesos.</p>
                        <p>Asimismo, se respetará en todo momento el derecho a la propia imagen reconocido en el
                          artículo
                          18 de la
                          Constitución española y art.4.2 regulado por la Ley 1/1982 de 5 de mayo, sobre el derecho al
                          honor, intimidad
                          personal y familiar y la propia imagen.</p>
                        <h5>¿Durante cuánto tiempo se conservan las grabaciones?</h5> En ciertos casos, las grabaciones
                        pueden ser
                        eliminadas una vez finalizados los procesos de validación de autoría y ausencia de ayuda
                        externa,
                        pudiendo ser
                        borrados en un plazo mínimo de una semana desde la grabación. En otros casos, las grabaciones se
                        deben almacenar
                        para eventuales procesos de acreditación ante entidades oficiales externas.En ambos casos, el
                        plazo máximo de
                        almacenamiento de las grabaciones será el legalmente establecido, de conformidad con art. 5.1 e)
                        del RGPD. <h5>
                          ¿Quién es el Responsable del Tratamiento de estas grabaciones?</h5>
                        <p>El responsable del tratamiento de las grabaciones es la FUNDACIÓN UNIVERSITARIA
                          IBEROAMERICANA
                          - FUNIBER (Paseo
                          García Faria, nº 29 08005 BARCELONA, con CIF G62060421, teléfono: 934 93 99 00 y correo
                          electrónico
                          dpo@funiber.org).</p>
                        <h5>¿Cómo puedo ejercer mis derechos?</h5>
                        <p>Los interesados tienen la posibilidad de ejercer los derechos de acceso, rectificación,
                          supresión, limitación
                          deltratamiento, portabilidad y oposición, de conformidad con lo dispuesto al respecto en la
                          normativa aplicable,
                          dirigiéndose porescrito al Responsable del Tratamiento en el domicilio anteriormente señalado,
                          indicando en el
                          asunto del comunicado:"Protección de Datos".</p>
                        <div ref="watchMoreTwo">
                          <v-card outlined elevation="0" v-show="watchMoreTwo">
                            <v-card-text>
                              <h4>DOCUMENTO PARA OBTENER EL CONSENTIMIENTO PARA LA IMAGEN PARA FINALIDADES DE CONTROL
                                ACADÉMICO SUPERVISADO.
                              </h4>
                              <p>En virtud del Reglamento General de Protección de Datos (UE) 679/2016, FUNDACIÓN
                                UNIVERSITARIA IBEROAMERICANA
                                (FUNIBER) (en adelante el Responsable del Tratamiento) Paseo García Faria, nº 29 08005
                                BARCELONA, con CIF
                                G62060421, teléfono: 934 93 99 00 ymail funiber@funiber.org, LE INFORMA:</p>
                              <p>Que mediante el presente documento precisa de su consentimiento para obtener su imagen
                                mediante grabaciones
                                audiovisuales,para las siguientes actividades que precisan de un control académico
                                supervisado:</p>
                              <ol>
                                <li>Realización de exámenes supervisados mediante un sistema de grabación audiovisual.
                                </li>
                                <li>Entrega de trabajos finales y/o defensa de tesis anteriores que precisen o se
                                  realicen
                                  mediante
                                  grabaciones audiovisuales.</li>
                                <li>Otras entregas de trabajos académicos, no incluidas entre las anteriores que
                                  precisen o se
                                  realicen
                                  mediante grabaciones audiovisuales.</li>
                              </ol>
                              <p>Dichas imágenes se podrán utilizar en procesos de acreditación ante entidades
                                acreditadoras,
                                como por ejemplo
                                la ANECA, delos procesos académicos de nuestra organización.</p>
                              <p>Igualmente, se podrán utilizar las imágenes para validar la autoría de los exámenes y
                                trabajos mencionados,
                                así como paraasegurar que el alumno no ha recibido ayuda externa en la realización de
                                los
                                mismos.</p>
                              <p>En todo momento, se respetará el derecho a la propia imagen reconocido en el artículo
                                18 de
                                la Constitución
                                española y art.4.2 regulado por la Ley 1/1982 de 5 de mayo, sobre el derecho al honor,
                                intimidad personal y
                                familiar y la propia imagen.</p>
                              <p>La base jurídica del tratamiento es el consentimiento expreso. Los destinatarios de la
                                información serán el
                                personalacadémico o administrativo de nuestra organización que tengan que supervisar los
                                exámenes o trabajos
                                realizados, así como elpersonal de las entidades acreditadoras antes mencionadas. El
                                plazo de
                                conversación
                                de los datos de carácter personal, será ellegalmente establecido, de conformidad con
                                art. 5.1
                                e) del RGPD.
                              </p>
                              <p>El hecho de no facilitar las imágenes grabadas al Responsable del
                                Tratamiento o a las entidades mencionadas, implica que nose pueda cumplir con la
                                prestación de
                                los servicios
                                objeto de la matriculación en el programa académico.</p>
                              <p>Los interesados tienen la posibilidad de ejercer los derechos de acceso, rectificación,
                                supresión, limitación
                                deltratamiento, portabilidad y oposición, de conformidad con lo dispuesto al respecto en
                                la
                                normativa
                                aplicable, dirigiéndose porescrito al Responsable del Tratamiento en el domicilio
                                anteriormente señalado,
                                indicando en el asunto del comunicado:"Protección de Datos".</p>
                              <p>Los interesados pueden revocar su consentimiento en cualquier momento y tienen derecho
                                a
                                presentar una
                                reclamación ante la autoridad de control competente.</p>
                            </v-card-text>
                          </v-card>
                        </div>
                        <div class="d-flex justify-end mt-2" v-if="enableSeeLess()">
                          <v-btn text @click="watchLess()">
                            Ver menos
                          </v-btn>
                        </div>
                      </v-card-text>
                    </v-card>
                  </div>
                  <div class="d-flex justify-end mt-2" v-if="enableWatchMore()">
                    <v-btn text @click="watchMore()">
                      Ver mas
                    </v-btn>
                  </div>
                </v-card-text>
              </v-card>

              <div>
                <div class="d-flex justify-center">
                  <v-checkbox v-model="checkbox" hide-details label="He leído y acepto las normas indicadas arriba.">
                  </v-checkbox>
                </div>
                <div class="d-flex justify-center">
                  <v-checkbox v-model="checkbox"
                    label="Permito que se realicen grabaciones audiovisuales en actividades académicas."></v-checkbox>
                </div>
              </div>

              <v-btn class="mb-2 ml-1" @click="nextStep(2)">
                Continue
              </v-btn>
            </v-stepper-content>
            <v-stepper-content step="3">
              <v-card class="mb-12"  min-height="200px" elevation="0">
                <CamInit></CamInit>
              </v-card>
              <v-btn class="mb-2 ml-1" @click="nextStep(3)">
                Continue
              </v-btn>
            </v-stepper-content>
            <v-stepper-content step="4">
              <v-card class="mb-12"  min-height="200px" elevation="0">
                <ScreenCap></ScreenCap>
              </v-card>
              <v-btn class="mb-2 ml-1" @click="nextStep(4)">
                Continue
              </v-btn>
            </v-stepper-content>
            <v-stepper-content step="5">
              <v-card class="mb-12"  min-height="200px" elevation="0">
                <SecondCam></SecondCam>
              </v-card>
              <v-btn class="mb-2 ml-1" @click="nextStep(5)">
                Continue
              </v-btn>
            </v-stepper-content>
            <v-stepper-content step="6">
              <v-card class="mb-12"  min-height="200px" elevation="0">
                <IdentificationDoc></IdentificationDoc>
              </v-card>
              <v-btn class="mb-2 ml-1" @click="nextStep(6)">
                Continue
              </v-btn>
            </v-stepper-content>
            <v-stepper-content step="7">
              <v-card class="mb-12"  min-height="200px" elevation="0">
                <v-card-text>
                  <v-container>
                    <v-row justify="center">
                      <v-col cols="12">
                        <div class="proctor_control" id="yui_3_17_2_1_1693584377136_75">
                          <div>
                            <h2>Iniciar el examen</h2>
                            <p>Aún no ha iniciado el examen, pulse el botón inferior para iniciarlo. Recuerde lo
                              siguiente: </p>
                            <ol>
                              <li>Una vez iniciado dispone de un tiempo limitado para hacerlo.</li>
                              <li>No visite otras páginas hasta que termine el examen.</li>
                              <li>Su rostro debe ser visible en todo momento.</li>
                              <li>No debe aparecer más de una persona en la imagen.</li>
                              <li>Deberá compartir su pantalla en todo momento.</li>
                              <li>Las incidencias detectadas deberán ser corregidas inmediatamente. En caso contrario el
                                examen puede ser bloqueado temporalmente</li>
                            </ol>
                          </div>
                        </div>
                      </v-col>
                    </v-row>
                  </v-container>
                </v-card-text>
              </v-card>
              <v-btn class="mb-2 ml-1" @click="nextStep(7)">
                Iniciar examen
              </v-btn>
            </v-stepper-content>
          </v-stepper-items>
        </v-stepper>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
  export default {
    name: 'App',

    data: () => ({
      watchMoreOne: false,
      watchMoreTwo: false,
      mainStep: 1,
      steps: [{
          id: 1,
          name: 'Reglas',
          rules: [() => false],
          complete: false
        },
        {
          id: 2,
          name: 'Normas',
          rules: [() => false],
          complete: false
        },
        {
          id: 3,
          name: 'Camara',
          rules: [() => false],
          complete: false
        },
        {
          id: 4,
          name: 'Pantalla',
          rules: [() => false],
          complete: false
        },
        {
          id: 5,
          name: 'Segunda camara',
          rules: [() => false],
          complete: false
        },
        {
          id: 6,
          name: 'Documento de identidad',
          rules: [() => false],
          complete: false
        },
        {
          id: 7,
          name: 'Inicio de examen',
          rules: [() => false],
          complete: false
        }
      ]
    }),
    methods: {
      nextStep(n) {
        if ((n + 1) <= 7) {
          this.mainStep = n + 1
          this.steps[n-1].complete = true;
        }
      },
      watchMore() {
        if (!this.watchMoreOne) {
          this.watchMoreOne = true

          setTimeout(() => {
              var body = document.body,
                html = document.documentElement;

              var height = Math.max(body.scrollHeight, body.offsetHeight,
                html.clientHeight, html.scrollHeight, html.offsetHeight);

              window.scrollTo({
                top: height,
                behavior: 'smooth',
              });
            }, 200);
        } else {
          if (!this.watchMoreTwo) {
            this.watchMoreTwo = true

            setTimeout(() => {
              var body = document.body,
                html = document.documentElement;

              var height = Math.max(body.scrollHeight, body.offsetHeight,
                html.clientHeight, html.scrollHeight, html.offsetHeight);

              window.scrollTo({
                top: height,
                behavior: 'smooth',
              });
            }, 200);
          }
        }
      },
      watchLess() {
        if (this.watchMoreTwo) {
          this.watchMoreTwo = false
        } else {
          if (this.watchMoreOne) {
            this.watchMoreOne = false
          }
        }
      },
      enableWatchMore() {
        if ((!this.watchMoreOne) || (this.watchMoreOne && !this.watchMoreTwo)) {
          return true;
        } else {
          return false;
        }
      },
      enableSeeLess() {
        if ((this.watchMoreOne)) {
          return true;
        } else {
          return false;
        }
      }
    },
    components: {
      CamInit: () => import('@/components/CamInit.vue'),
      ScreenCap: () => import('@/components/ScreenCap.vue'),
      SecondCam: () => import('@/components/SecondCam.vue'),
      IdentificationDoc: () => import('@/components/IdentificationDoc.vue')
    }
  };
</script>

<style>
.v-stepper__header{
  box-shadow: none;
}
</style>