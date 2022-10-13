
<template>
    <div>
        <div class="toolBar">
            <div class="toolBar-item">
                <button class="toolBar-btn toolBar-start" data-cmd="bold"><i class="fa-sharp fa-solid fa-bold"></i></button>
                <button class="toolBar-btn" data-cmd="italic"><i class="fa-sharp fa-solid fa-italic"></i></button>
                <button class="toolBar-btn" data-cmd="strikeThrough"><i class="fa-sharp fa-solid fa-strikethrough"></i></button>
                <button class="toolBar-btn toolBar-end" data-cmd="underline"><i class="fa-sharp fa-solid fa-underline"></i></button>
            </div>
            <div class="toolBar-item">
                <button class="toolBar-btn toolBar-start" data-cmd="justifyLeft"><i class="fa-solid fa-align-left"></i></button>
                <button class="toolBar-btn" data-cmd="justifyCenter"><i class="fa-solid fa-align-center"></i></button>
                <button class="toolBar-btn" data-cmd="justifyRight"><i class="fa-solid fa-align-right"></i></button>
                <button class="toolBar-btn toolBar-end"><i class="fa-solid fa-align-justify" data-cmd="justifyFull"></i></button>
            </div>
            <div>
                <select v-model="font" id="fontes" class="toolBar-select">
                    <option disabled value="">Selecione uma fonte</option>
                    <option value="Arial">Arial</option>
                    <option value="Calibre">Calibre</option>
                    <option value="Century Gothic">Century Gothic</option>
                </select>
            </div>
        </div>
        <iframe name="textField" class="textContainer" frameborder="0"></iframe>
    </div>
</template>

<script>
    export default{
        data(){
            return{
                font:''
            }
        },
        mounted(){
            textField.document.designMode = 'On';
            const buttons = document.querySelectorAll('button');
            // Eventos nos botões
            for(let i=0; i < buttons.length; i++){
                let cmd = buttons[i].getAttribute('data-cmd')
                buttons[i].addEventListener('click', () => {
                    if(cmd == 'justifyLeft' || cmd == 'justifyRight' || cmd == 'justifyCenter' || cmd == 'justifyFull'){
                        textField.document.execCommand(cmd, false, null)
                    }else{
                        textField.document.execCommand(cmd, false, null)
                        //buttons[i].classList.toggle('active')
                    }
                })
            };
            //Evento no select
            document.getElementById('fontes').addEventListener('change', () => {
                console.log(this.font)
                textField.document.execCommand('fontname', false, this.font)
            })
        },
    }
</script>

<style lang="sass">
    .toolBar
        display: flex
        flex-direction: row

        &-item
            margin-right: 0.5rem

        &-start
            border-start-start-radius: 10%
            border-end-start-radius: 10%
        &-end
            border-end-end-radius: 10%
            border-start-end-radius: 10% 
        &-btn
            padding: 0.4rem
            height: 100%
            border: 0.1rem solid
            border-collapse: collapse
            box-sizing: border-box

            &:hover
                cursor: pointer
                border: 0.15rem solid blue
                
        &-select
            padding: 0.4rem
            height: 100%
            width: 100%
    .active
        border-color: blue

.textContainer
    width: 30rem
    border: 0.1rem solid black
    border-radius: 1%
button
    border: none
</style>