<template>

<transition name="fade" appear>
        <div class="modal-back" @click.self="$emit('close')">
            <div class="modal-wrapper">
                <div class="modal-header">
                    <h3>C'est quoi Emoji Concept ?</h3>
                    <button class="close" @click="$emit('close')">&times;</button>
                </div>
                <div class="modal-body">
                    <div class="message">
                        <p>C'est une adaptation avec des emojis du jeu de plateau Concept. Le but est de faire deviner un mot, une expression, un film, etc,  en utilisant des emojis.</p>
                        <p>Chaque emoji possède un sens indiqué sur cette page. Le but est de les associer en concepts et sous-concepts. La première ligne décrit le concept principal, et chaque  autre ligne un sous-concept lié.</p>
                        <h4>Exemple : </h4>
                        <pre>
🏢🔩

┗ 🚩🔵⚪🔴
                        </pre>
                        La première ligne (concept principal) indique qu'on cherche un bâtiment (🏢) métallique (🔩).<br>
                        La seconde ligne (sous-concept) indique qu'il se situe dans un lieu/pays (🚩) dont les couleurs sont bleu/blanc/rouge (🔵⚪🔴).<br>
                        C'était donc la <strong>Tour Eiffel</strong> !

                    </div>
                </div>
                <div class="buttons">
                    <button class="go"  @click="$emit('close')">Ok, on joue ?</button>
                </div>
            </div>
        </div>
    </transition>

</template>


<style scoped>
.modal-back {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0,0,0,0.5);
    z-index: 10;
}   
.modal-wrapper {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 80%;
    max-width: 850px;
    background-color: #fff;
    border-radius: 5px;
    padding: 1rem;
    max-height: 90%;
    overflow-y: scroll;
}
.modal-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.modal-header h3 {
    margin: 0;
    font-size: 2rem;
    margin-bottom: 1rem;
}
.modal-header button {
    border: none;
    background: none;
    cursor: pointer;
}

.close {
    font-size: 3rem;
    padding: 0;
    line-height: 1;
    position: absolute;
    right: 1rem;
    top: .5rem;
}
p {
    margin-top: 0;
}

.message {
    font-size: 1.7rem;
    line-height: 1; 
}
.code {
    padding: 1rem;
    width: 100%;
}
.buttons {
    display: flex;
    justify-content: center;
    margin-top: 1rem;
}
</style>