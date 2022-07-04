<template>
    <form @submit.prevent="handleSubmit">
        <label>Imię:</label>
        <input type="text" required v-model="name">

        <label>Nazwisko:</label>
        <input type="text" required v-model="lastname">

        <label>Email:</label>
        <input type="email" required v-model="email">

        <label>Hasło:</label>
        <input type="password" required v-model="password">
        <div v-if="passwordError" class="error">{{ passwordError }}</div>

        <label>Wykształcenie:</label>
        <select v-model="role">
            <option value="podstawowe">wykształcenie podstawowe</option>
            <option value="gimnazjalne">wykształcenie gimnazjalne</option>
            <option value="zasadnicze zawodowe">wykształcenie zasadnicze zawodowe</option>
            <option value="zasadnicze branżowe">wykształcenie zasadnicze branżowe</option>
            <option value="średnie branżowe">wykształcenie średnie branżowe</option>
            <option value="średnie">wykształcenie średnie</option>
            <option value="wyższe">wykształcenie wyższe</option>
        </select>

        <div class="terms">
            <input type="checkbox" v-model="terms" required>
            <label>Akceptuje regulamin</label>
       </div>

       <div class="submit">
           <button>Zarejestruj się</button>
       </div>
    </form>
    
</template>

<script>
export default {
    data() {
        return{
            name: '',
            lastname:'',
            email: '',
            password: '',
            role:'',
            terms:'folse',
            passwordError:''
            
        }
    },
    methods: {
        handleSubmit() {
            // validate password
            this.passwordError = this.password.length > 7 ?
            '' : 'Hasło musi zawierać minimum 8 znaków'

            if(!this.passwordError) {
                console.log('name: ', this.name)
                console.log('lastname: ', this.lastname)
                console.log('email: ', this.email)
                console.log('password: ', this.password)
                console.log('role: ', this.role)
                console.log('terms accepted: ', this.terms)}

        }
    }

}
</script>

<style>
form {
        max-width: 420px;
        margin: 30px auto;
        background: rgb(241, 241, 241);
        text-align: left;
        padding: 40px;
        border-radius: 10px;
}
label {
    color:#aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}
input, select {
display: block;
padding: 10px 6px;
width: 100%;
box-sizing: border-box;
border: none;
border-bottom: 1px solid #ddd;
color: #555
}
input[type="checkbox"]{
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
}
button{
    background:rgb(197, 43, 43);
    border: 0;
    padding: 20px 20px;
    margin-top: 30px;
    color:white;
    border-radius:20px;
    font-weight: bold
}
.submit{
    text-align: center;
    
}
.error{
    color:red;
    margin-top:10px;
    font-size:0.6em;
    font-weight: bold
}
</style>
 