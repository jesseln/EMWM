<template>
    <div >
    <!-- <div class="shelf-separator-container"><div class="shelf-separator"></div></div> -->

    <NuxtPage :setQuery="agent01" />

    <div v-if="viewStore.formattedLibrary.length">
        <LibraryView />
    </div>

    <button @click="showAnnotations=!showAnnotations" class="annotation-button" :class="{ 'active': showAnnotations }">
        🖊️
    </button>
    <AnnotationPanel v-if="showAnnotations"/>
    <button ref="toTopButton" @click="scrollToTop" class="to-top-button">☝️</button>
    </div>
   
    
  </template>
  
  <script setup>


  //Library State
  const libraryStore = useLibraryStore();
  //View State
  const viewStore = useViewStore();
//   const { width, height } = useWindowSize()
  const showAnnotations = ref(false)

    // To Top Button
    const { x, y } = useWindowScroll() // To replace below
    const useX = x
    const useY = y
    const toTopButton = ref();
    onMounted(() => {
        watchEffect(()=>{
            if (useY.value > 550) {
                toTopButton.value.classList.add("showButton");
            } else {
                toTopButton.value.classList.remove("showButton");
            }
        })
    })
    const scrollToTop = () => {
        window.scrollTo({ top: 0, behavior: "smooth" });
    };


  </script>
  
  <style scoped>
  

  </style>