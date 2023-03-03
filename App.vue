<template>
    <div class="mainApp">
        <!-- <post-form/>
        <post-list :posts="posts"/> -->
                
        <form @submit.prevent>
            <h4>Назначение постов</h4>

            <input
            v-bind:value="title"
            @input="title = $event.target.value"
            class="input"
            type="text"
            placeholder="Name for post"
            >

            <input
            v-bind:value="body"
            @input="body = $event.target.value"
            class="input"
            type="text"
            placeholder="Content for post"
            >

            <button class="submit" @click="addPost">Добавить пост</button>
            <button class="submit" @click="deletePost">Удалить пост </button>
            </form>



            <div class="post" v-for="post in posts">
                <div><strong>Название: </strong> {{ post.title }}</div>
                <div><strong>Описание: </strong>{{ post.body }}</div>
            </div>



    </div>
</template>

<script>
import form from './components/form.vue';
import list from './components/list.vue';
export default{
    components:{
      form, list 
    },
    data(){
        return{          
            posts: [
                {id: 1, title: 'Статья о JavaScript', body: 'Сам JavaScript'},
                {id: 2, title: 'Статья о JavaScript', body: 'Сам JavaScript'},
                {id: 3, title: 'Статья о JavaScript', body: 'Сам JavaScript'},
                {id: 4, title: 'Статья о Java', body: 'Сам Java'},
            ],
            title: "",
            
            body: ""
        }
    },
    methods:{
        addPost(event){
            let newPost = {
                id: Date.now(),
                title: this.title,
                body: this.body,
            }
            this.posts.push(newPost);
            this.title = "";
            this.body = "";
        },
        deletePost(index){
            // if(input==""){
            //     alert("Введите текст для удаления");
            // }else{
            //     confirm("Вы уверены что хотите удалить этот пост?");
            //     if(confirm){
            //         this.posts.splice(index, 1);
            //     }
            // }

            this.posts.splice(index, 1);

        }
            
        }
        
    }
</script>

<style>

    *{
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }
    .mainApp{
        padding: 20px;
    }
    .input{
        width: 100%;
        padding: 0.5em;
        margin-bottom: 1em;
        border: 1px solid #3bb914;
        border-radius: 5px;
    }
    form{
        display: flex;
        flex-direction: column;
    }
    .submit{
        margin-top: 15px;
        align-self: flex-end;
        padding: 0.5em;
        border: 1px solid #3bb914;
        border-radius: 5px;
        background-color: #3bb914;
        color: white;
    }
    .post{
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        background-color: #f2f2f2;
        border: 3px solid #3bb914;
        padding: 1em;
        margin-top: 20px;
    }
</style>
