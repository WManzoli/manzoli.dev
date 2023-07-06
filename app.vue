<template>
  <Head>
    <Title>wmanzoli</Title>
    <Meta
        name="wmanzoli"
        content="Personal website."
    />
    <Link rel="icon" type="image/png" sizes="32x32" href="/icons/favicon.ico"></Link>
  </Head>
  <div class="container">
    <div class="first-component">
      <div id="canvas-container" v-on:click="changeTheme()">
        <canvas id="globe-canvas" />
      </div>
      <div class="info">
        <p class="name">{{profile.user.name}}</p>
        <p class="role">{{profile.user.role}}</p>
        <p class="living-at">
          <img
              style="width: 32px; padding-right: 16px"
              class="interaction"
              :src="'/icons/' + profile.user.flag"
          />
          {{profile.user['living-at']}}
        </p>
        <div class="contacts">
          <a href="https://www.linkedin.com/in/wmanzoli/" target="_blank">
            <svg
                class="interaction"
                aria-hidden="true"
                focusable="false"
                data-prefix="fab"
                data-icon="linkedin"
                role="img"
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 512 512"
                style="width: 32px; padding: 1rem"
            >
              <path
                  :fill="isDark ? '#fff' : '#000'"
                  d="M416 32H31.9C14.3 32 0 46.5 0 64.3v383.4C0 465.5 14.3 480 31.9 480H416c17.6 0 32-14.5 32-32.3V64.3c0-17.8-14.4-32.3-32-32.3zM135.4 416H69V202.2h66.5V416zm-33.2-243c-21.3 0-38.5-17.3-38.5-38.5S80.9 96 102.2 96c21.2 0 38.5 17.3 38.5 38.5 0 21.3-17.2 38.5-38.5 38.5zm282.1 243h-66.4V312c0-24.8-.5-56.7-34.5-56.7-34.6 0-39.9 27-39.9 54.9V416h-66.4V202.2h63.7v29.2h.9c8.9-16.8 30.6-34.5 62.9-34.5 67.2 0 79.7 44.3 79.7 101.9V416z"
              ></path>
            </svg>
          </a>
          <a href="mailto:williammanzoli@gmail.com">
            <svg
                class="interaction"
                aria-hidden="true"
                focusable="false"
                data-prefix="far"
                data-icon="envelope"
                role="img"
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 512 470"
                style="width: 37px; padding: 1rem"
            >
              <path
                  :fill="isDark ? '#fff' : '#000'"
                  d="M464 64H48C21.49 64 0 85.49 0 112v288c0 26.51 21.49 48 48 48h416c26.51 0 48-21.49 48-48V112c0-26.51-21.49-48-48-48zm0 48v40.805c-22.422 18.259-58.168 46.651-134.587 106.49-16.841 13.247-50.201 45.072-73.413 44.701-23.208.375-56.579-31.459-73.413-44.701C106.18 199.465 70.425 171.067 48 152.805V112h416zM48 400V214.398c22.914 18.251 55.409 43.862 104.938 82.646 21.857 17.205 60.134 55.186 103.062 54.955 42.717.231 80.509-37.199 103.053-54.947 49.528-38.783 82.032-64.401 104.947-82.653V400H48z"
              ></path>
            </svg>
          </a>
          <a href="https://www.github.com/wmanzoli" target="_blank">
            <svg
                class="interaction"
                aria-hidden="true"
                focusable="false"
                data-prefix="fab"
                data-icon="github"
                role="img"
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 520 520"
                style="width: 32px; padding: 1rem"
            >
              <path
                  :fill="isDark ? '#fff' : '#000'"
                  d="M165.9 397.4c0 2-2.3 3.6-5.2 3.6-3.3.3-5.6-1.3-5.6-3.6 0-2 2.3-3.6 5.2-3.6 3-.3 5.6 1.3 5.6 3.6zm-31.1-4.5c-.7 2 1.3 4.3 4.3 4.9 2.6 1 5.6 0 6.2-2s-1.3-4.3-4.3-5.2c-2.6-.7-5.5.3-6.2 2.3zm44.2-1.7c-2.9.7-4.9 2.6-4.6 4.9.3 2 2.9 3.3 5.9 2.6 2.9-.7 4.9-2.6 4.6-4.6-.3-1.9-3-3.2-5.9-2.9zM244.8 8C106.1 8 0 113.3 0 252c0 110.9 69.8 205.8 169.5 239.2 12.8 2.3 17.3-5.6 17.3-12.1 0-6.2-.3-40.4-.3-61.4 0 0-70 15-84.7-29.8 0 0-11.4-29.1-27.8-36.6 0 0-22.9-15.7 1.6-15.4 0 0 24.9 2 38.6 25.8 21.9 38.6 58.6 27.5 72.9 20.9 2.3-16 8.8-27.1 16-33.7-55.9-6.2-112.3-14.3-112.3-110.5 0-27.5 7.6-41.3 23.6-58.9-2.6-6.5-11.1-33.3 2.6-67.9 20.9-6.5 69 27 69 27 20-5.6 41.5-8.5 62.8-8.5s42.8 2.9 62.8 8.5c0 0 48.1-33.6 69-27 13.7 34.7 5.2 61.4 2.6 67.9 16 17.7 25.8 31.5 25.8 58.9 0 96.5-58.9 104.2-114.8 110.5 9.2 7.9 17 22.9 17 46.4 0 33.7-.3 75.4-.3 83.6 0 6.5 4.6 14.4 17.3 12.1C428.2 457.8 496 362.9 496 252 496 113.3 383.5 8 244.8 8zM97.2 352.9c-1.3 1-1 3.3.7 5.2 1.6 1.6 3.9 2.3 5.2 1 1.3-1 1-3.3-.7-5.2-1.6-1.6-3.9-2.3-5.2-1zm-10.8-8.1c-.7 1.3.3 2.9 2.3 3.9 1.6 1 3.6.7 4.3-.7.7-1.3-.3-2.9-2.3-3.9-2-.6-3.6-.3-4.3.7zm32.4 35.6c-1.6 1.3-1 4.3 1.3 6.2 2.3 2.3 5.2 2.6 6.5 1 1.3-1.3.7-4.3-1.3-6.2-2.2-2.3-5.2-2.6-6.5-1zm-11.4-14.7c-1.6 1-1.6 3.6 0 5.9 1.6 2.3 4.3 3.3 5.6 2.3 1.6-1.3 1.6-3.9 0-6.2-1.4-2.3-4-3.3-5.6-2z"
              ></path>
            </svg>
          </a>
        </div>
      </div>
    </div>
    <div class="second-component">
        <div class="techs">
          <div class="topics-div">
            <div class="topics-titles">STUDIES</div>
          </div>
          <div class="icons">
            <div
                v-for="(icon, index) in profile.jobs.icons"
                :key="index"
                style="display: flex; flex-direction: column; justify-content: flex-end; align-items: center; gap: 1rem;"
            >
              <img class="interaction"
                   width="23px" style="margin-right: 1rem;"
                   :src="'/icons/' + icon.src"
              />
            </div>
          </div>
        </div>
        <div class="studies">
          <div style="width: 400px; margin: 0 0 1rem 0;">
            <a
                href="https://portal.fmu.br/"
                target="_blank"
                style="
                display: flex;
                align-items: center;
                justify-content: flex-start;
            "
            >
              <img
                  class="university-photo"
                  :src="'/icons/' + profile.education[0].src"
              />
              <div style="">
                <div
                    style="
                  display: flex;
                  flex-direction: column;
                  align-items: flex-start;
                  justify-content: center;
                "
                >
                  <div style="padding-left: 1rem">
                    <p class="course-name">{{profile.education[0].course}}</p>
                    <p class="university-name">
                      {{profile.education[0].university}}
                    </p>
                    <p class="course-date">{{profile.education[0].date}}</p>
                  </div>
                </div>
              </div>
            </a>
          </div>
          </div>
        <div class="jobs">
          <div class="topics-div">
            <div class="topics-titles">TRUSTED BY</div>
          </div>
          <div class="companys">
            <div
                v-for="(company, index) in profile.companies"
                :key="index"
                style="width: 33%;"
            >
              <a :href="company.link" target="_blank">
                <img
                    :class="company.name + ' interaction'"
                    :width="company.width"
                    :src="isDark ? '/icons/dark/' + company.src  : '/icons/light/' + company.src "
                />
              </a>
            </div>
          </div>
          </div>
        <div class="recommendations">
          <div
              style="
              display: flex;
              flex-direction: column;
              align-items: center;
              justify-content: flex-start;
              width: 100%;
            "
          >
            <div
                style="
                display: flex;
                align-items: center;
                justify-content: flex-start;
                width: 100%;
                min-height: 15vh;
              "
            >
              <img
                  id="recom"
                  class="recommendation-photo"
                  :src="profile.references[currentRecommendation]['picture']"
              />
              <div style="width: 100%">
                <div
                    style="
                    display: flex;
                    flex-direction: column;
                    align-items: flex-start;
                    justify-content: center;
                    width: 100%;
                    padding: 1rem 0;
                  "
                >
                  <div style="padding-left: 1rem">
                    <p class="recommendation-name">
                      {{ profile.references[currentRecommendation]['name'] }}
                    </p>
                    <p class="recommendation-role">
                      {{ profile.references[currentRecommendation]['role'] }}
                    </p>
                    <p id="recom" class="recommendation-text">
                      "{{ profile.references[currentRecommendation]['text'] }}"
                    </p>
                  </div>
                </div>
              </div>
            </div>
            <div
                style="
                display: flex;
                align-items: center;
                justify-content: center;
                gap: 1rem;
              "
            >
              <span v-for="(item, index) in profile.references" :key="index">
                <div
                    @click="setRecommendation(index)"
                    :style="index === currentRecommendation ? 'width: 10px; height: 10px; background: white; border-radius: 16px; border: 1px solid gray' : 'width: 10px; height: 10px; background: gray; border-radius: 16px;'"
                />
              </span>
            </div>
          </div>
        </div>
    </div>
  </div>
</template>
<script>
import { onMounted, ref, nextTick } from 'vue'
import profile from './public/profile.json';
import * as THREE from 'three';
import { OrbitControls } from "three/examples/jsm/controls/OrbitControls.js";

export default {
  setup() {

    const textureURLs = {
      dark: "/textures/night-world.png",
      light: "/textures/day-world.png"
    };
    const textureURL = ref(textureURLs.light);
    const displacementURL = ref("/displacement.png");
    const isDark = ref(false)
    const currentRecommendation = ref(0)
    let scene, camera, renderer, earth, material, controls;

    const changeTheme = () => {
      const html = document.getElementsByTagName('html')[0]
      if(isDark.value === true) {
        isDark.value = false
        html.classList.remove('dark-mode')
        textureURL.value = textureURLs.light;
      } else {
        isDark.value = true
        html.classList.add('dark-mode')
        textureURL.value = textureURLs.dark;
      }
      updateTexture();
      html.classList.toggle('fade')
    }
    const setRecommendation = (value) => {
      const recom = document.getElementById('recom')
      currentRecommendation.value = value
      recom.classList.toggle('fade')
    }
    const updateTexture = () => {
      const textureLoader = new THREE.TextureLoader();
      const newTexture = textureLoader.load(textureURL.value);
      material.map = newTexture;
      material.needsUpdate = true;
    };

    onMounted(() => {
      scene = new THREE.Scene();
      camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.01, 1000);

      const globe = document.getElementById("globe-canvas");
      renderer = new THREE.WebGLRenderer({
        canvas: globe,
        antialias: true,
        alpha: true
      });
      renderer.setClearColor (0xffffff, 0);

      let containerWidth = document.getElementById('canvas-container').clientWidth;
      let containerHeight = document.getElementById('canvas-container').clientHeight;
      renderer.setSize(containerWidth, containerHeight);

      controls = new OrbitControls(camera, globe);
      controls.enablePan = false;

      document.getElementById('canvas-container').appendChild(renderer.domElement);

      const geometry = new THREE.SphereGeometry(2, 120, 120);

      const textureLoader = new THREE.TextureLoader();
      const texture = textureLoader.load(textureURL.value);
      const displacementMap = textureLoader.load(displacementURL.value);
      material = new THREE.MeshPhongMaterial({
        color: 0xffffff,
        map: texture,
        displacementMap: displacementMap,
        displacementScale: 0.06,
        bumpMap: displacementMap,
        bumpScale: 0.5,
        reflectivity: 0,
        shininess: 0,
      });

      earth = new THREE.Mesh(geometry, material);

      const light = new THREE.DirectionalLight(0xFFFFFF, 1);
      light.position.set(-100, 10, 50);
      scene.add(light);

      const hemiLight = new THREE.HemisphereLight(0xffffff, 0xffffff, 1);
      hemiLight.color.setHSL(1, 1, 1);
      hemiLight.groundColor.setHSL(1, 1, 1);
      hemiLight.position.set(0, 0, 0);
      scene.add(hemiLight);

      const worldGeometry = new THREE.SphereGeometry(500, 60, 60);
      const worldMaterial = new THREE.MeshBasicMaterial({
        color: 0xffffff,
        opacity: 0,
        transparent: true
      });
      const world = new THREE.Mesh(worldGeometry, worldMaterial);

      scene.add(world);
      scene.add(earth);

      earth.rotation.x = 3.1415 * 0.02;
      earth.rotation.y = 3.1415 * 1.54;

      function animate() {
        requestAnimationFrame(animate);
        earth.rotation.y += 0.002;
        earth.rotation.x += 0.0001;
        world.rotation.y += 0.0001;
        world.rotation.x += 0.0005;
        renderer.render(scene, camera);
      }
      function onResize() {
        containerWidth = document.getElementById('canvas-container').clientWidth;
        containerHeight = document.getElementById('canvas-container').clientHeight;
        camera.aspect = containerWidth / containerHeight;
        camera.updateProjectionMatrix();
        renderer.setSize(containerWidth, containerHeight);
        camera.position.z = 3.5
      }

      window.addEventListener('resize', onResize, false);
      nextTick(() => {
        onResize();
      })

      setInterval(function () {
        if (currentRecommendation.value < profile.references.length - 1) {
          setRecommendation(currentRecommendation.value + 1)
        } else {
          setRecommendation(0)
        }
      }, 7000); // 7s

      onResize()
      animate();
    });

    return {
      profile,
      currentRecommendation,
      setRecommendation,
      changeTheme,
      isDark
    };
  }
}
</script>
<style>
a {
  text-decoration: transparent;
}
img {
  background-color: transparent;
}
html,
body,
html * {
  background-color: var(--bg);
  color: var(--color);
  transition: background-color 0.3s;
  -webkit-user-select: none;
  -moz-user-select: none;
  user-select: none;
  -webkit-touch-callout: none;
  box-sizing: content-box;
  scrollbar-face-color: gray;
  scrollbar-base-color: gray;
  scrollbar-3dlight-color: gray;
  scrollbar-highlight-color: gray;
  scrollbar-track-color: #fff;
  scrollbar-arrow-color: #fff;
  scrollbar-shadow-color: gray;
  scrollbar-dark-shadow-color: gray;
  font-family: "Roboto", sans-serif;
  margin: 0;
  padding: 0;
  -webkit-animation: fadein 1s; /* Safari, Chrome and Opera > 12.1 */
  -moz-animation: fadein 1s; /* Firefox < 16 */
  -ms-animation: fadein 1s; /* Internet Explorer */
  -o-animation: fadein 1s; /* Opera < 12.1 */
  animation: fadein 1s;
}
:root {
  --color: #000;
  --color-primary: #fff;
  --color-secondary: #000;
  --bg: #f3f5f4;
  --bg-secondary: #fff;
  --border-color: #ddd;
}
.dark-mode {
  --color: #ebf4f1;
  --color-primary: #41b38a;
  --color-secondary: #fdf9f3;
  --bg: #000;
  --bg-secondary: #071521;
  --border-color: #0d2538;
}
@media screen and (max-width: 920px) {
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  .first-component {
    z-index: 2;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    width: 100%;
  }
  .info {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 90%;
  }
  .name {
    font-weight: bold;
    font-size: 1.3rem;
    letter-spacing: 0.5rem;
  }
  .role {
    font-weight: normal;
    font-size: 1.2rem;
    letter-spacing: 0.25rem;
  }
  #canvas-container {
    width: 100vw !important;
    height: 35vh !important;
    cursor: pointer;
    z-index: 1;
    position: relative;
    background: transparent;
  }
  .second-component {
    z-index: 2;
    width: 90vw;
    min-height: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  .topics-div {
    margin: 0.5rem 0 0 0;
    display: flex;
    font-weight: bolder;
    font-size: 1rem;
    letter-spacing: 0.1rem;
  }
  .topics-titles {
    font-size: 0.7rem;
    letter-spacing: 1.5rem;
    display: flex;
    align-items: flex-end;
    font-weight: bold;
    color: gray;
  }
  .companys {
    margin: 1rem 0 0 0;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    gap: 2vw;
  }
  .contacts {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
}
@media screen and (min-width: 921px) {
  .container {
    z-index: -2;
    display: flex;
    width: 90vw;
    height: 90vh;
    padding: 5vh 5vw;
  }
  .first-component {
    z-index: 2;
    width: 45vw;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }
  .info {
    display: flex;
    flex-direction: column;
    align-items: center;
    min-height: 50%;
  }
  .name {
    font-weight: bold;
    font-size: 2rem;
    letter-spacing: 0.3vw;
  }
  .role {
    font-weight: normal;
    font-size: 1.5rem;
    letter-spacing: 0.25rem;
  }
  #canvas-container {
    margin-top: 9rem;
    width: 50vw !important;
    height: 50vh !important;
    cursor: pointer;
    z-index: 1;
    position: relative;
    background: transparent;
  }
  .second-component {
    z-index: 2;
    width: 35vw;
    height: 80vh;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }
  .topics-div {
    display: flex;
    font-weight: bolder;
    font-size: 1rem;
    letter-spacing: 0.1rem;
  }
  .topics-titles {
    font-size: 0.7rem;
    letter-spacing: 1.5rem;
    display: flex;
    align-items: flex-end;
    font-weight: bold;
    color: gray;
  }
  .companys {
    display: flex;
    align-items: center;
    justify-content: flex-start;
    margin: 1rem 0 0 0;
  }
  .contacts {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
}
.living-at {
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: lighter;
  font-size: 0.9rem;
  letter-spacing: 0.1rem;
}
.icons {
  display: flex;
  margin: 1rem 0;
}
.techs {
  width: 100%;
  font-size: 1rem;
  letter-spacing: 0.1rem;
}
.jobs {
  width: 100%;
  font-weight: lighter;
  font-size: 1rem;
  letter-spacing: 0.1rem;
  margin-top: 3rem;
}
.recommendations {
  width: 100%;
  font-weight: lighter;
  font-size: 1rem;
  letter-spacing: 0.1rem;
}
.recommendation-photo {
  width: 64px;
  min-height: 64px;
  border-radius: 64px;
}
.recommendation-name {
  font-size: 1.2rem;
  font-weight: bolder;
}
.recommendation-role {
  font-size: 1rem;
  font-weight: lighter;
}
.recommendation-text {
  font-size: 0.8rem;
  font-weight: normal;
}
.university-photo {
  width: 64px;
  min-height: 64px;
}
.studies {
  width: 100%;
  font-weight: lighter;
  font-size: 1rem;
  letter-spacing: 0.1rem;
}
.course-name {
  font-size: 1rem;
}
.university-name {
  font-size: 0.8rem;
}
.course-date {
  font-size: 0.8rem;
}
.interaction {
  cursor: pointer;
  transition: transform 0.2s; /* Animation */
}
.interaction:hover {
  transform: scale(
      1.10
  );
}
.fade {
  -webkit-animation: fade 1500ms ease-in;
  animation: fade 1500ms ease-in;
  -webkit-animation-iteration-count: 1;
  animation-iteration-count: 1;
}
::selection {
  color: white;
  background: black;
}
::-moz-selection {
  color: white;
  background: black;
}
::-webkit-scrollbar {
  width: 8px;
  height: 3px;
}
::-webkit-scrollbar-track {
  background-color: gray;
}
::-webkit-scrollbar-track-piece {
  background-color: #fff;
}
::-webkit-scrollbar-thumb {
  height: 50px;
  background-color: #fff;
  border-radius: 3px;
  border: 1px solid gray;
}
::-webkit-scrollbar-corner {
  background-color: gray;
}
::-webkit-resizer {
  background-color: gray;
}
@keyframes fade {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
@keyframes fadein {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@-moz-keyframes fadein {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@-webkit-keyframes fadein {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@-ms-keyframes fadein {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@-o-keyframes fadein {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>
