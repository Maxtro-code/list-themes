  <script setup>

  import {ref} from 'vue';

  const nouveauTheme = ref('');
  const listeThemes = ref([]);
  let listeThemeIdentifiant = 0;

  const ajouteNouveauTheme = () => {
  listeThemes.value.push({
    id: listeThemeIdentifiant,
    effectue: false,
    contenu: nouveauTheme.value,
  });
  nouveauTheme.value = '';
  listeThemeIdentifiant++;
};

  const basculeEtudie = () => {

};

  const onEnter = () => {
 ajouteNouveauTheme()
};
</script>

<template>
  <div>
    <h1 class="text-center">Liste de Thèmes à étudier</h1>
    <div>
      <!-- V-model ajoute un écouteur d'événement sur la saisie et met à jour la variable réactive nouveauTheme -->
      <!-- la variable reactive nouveauTheme est automatiquement mise à jour également -->
      <input v-model="nouveauTheme" @keyup.enter="onEnter" name="nouveauTheme" type="text"
             placeholder="Nouveau thème ... ">
      <button @click="ajouteNouveauTheme">Ajouter un thème</button>
    </div>
    <ul>
      <!-- V-for répète la balise HTML li pour chaque thème dans la liste de thèmes -->
      <!-- le : est un raccourci pour l'instruction v-bind qui permet de lier la liste à l'identifiant -->
      <!-- ce qui nous permettra ensuite de supprimer un élément sans perdre le fil -->
      <li v-for="(theme, index) in listeThemes" :key="theme.id">
        <div>
          <!-- L'attribut de classe de style est lié à la propriété effectuée du thème -->
          <!--aura la classe .effectue appliquée si la propriété effectuée de theme est évaluées à true -->
          <p :class="{ effectue: theme.effectue }">{{ theme.contenu }}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.effectue {
  text-decoration: line-through;
}
</style>