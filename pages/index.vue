<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-5 coloum">
                <form>
                    <div class="form-group">
                        <label for="name" class="form-group-name">
                            Nama
                        </label>
                        <input v-model="name" type="text" @keypress="handleKeypress('name')" class="form-control name" id="name" placeholder="Contoh: Andrew Justin">
                        <small id="error-name" class="form-text text-muted" style="color: red !important" v-if="errorName">{{ errorName }}</small>
                    </div>
                    <div class="form-group gender">
                        <label for="jenis-kelamin">
                            Jenis Kelamin
                        </label>
                        <div class="custom-control custom-radio">
                            <input v-model="gender" type="radio" class="custom-control-input" id="defaultUnchecked" value="Laki-laki" name="defaultExampleRadios">
                            <label class="custom-control-label" for="defaultUnchecked">
                                Laki - laki
                            </label>
                        </div>
                        <div class="custom-control custom-radio">
                            <input v-model="gender" type="radio" class="custom-control-input" id="defaultChecked" value="perempuan" name="defaultExampleRadios">
                            <label class="custom-control-label" for="defaultChecked">
                                Perempuan
                            </label>
                            <small id="error-gender" class="form-text text-muted" style="color: red !important" v-if="errorGender">{{ errorGender }}</small>
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="hobby" class="form-check-hobby">Hobbi</label>
                            <div class="form-check">
                                <input v-model="hobby" class="form-check-input" type="checkbox" value="music" id="music">
                                <label for="music">
                                    Musik
                                </label>
                            </div>
                            <div class="form-check">
                                <input v-model="hobby" class="form-check-input" type="checkbox" value="football" id="football">
                                <label for="football">
                                    Sepak Bola
                                </label>
                            </div>
                            <div class="form-check">
                                <input v-model="hobby" class="form-check-input" type="checkbox" value="tennis" id="tennis">
                                <label  for="tennis">
                                    Tennis
                                </label>
                            </div>
                            <div class="form-check">
                                <input v-model="hobby" class="form-check-input" type="checkbox" value="badminton" id="badminton">
                                <label for="badminton">
                                    Badminton
                                </label>
                            </div>
                            <small id="error-Hobby" class="form-text text-muted" style="color: red !important" v-if="errorHobby">{{ errorHobby }}</small>
                    </div>
                    <div class="form-group">
                        <label for="exampleFormControlInput1">
                            Email
                        </label>
                        <input v-model="email" @keypress="handleKeypress('email')" type="email" class="form-control" id="exampleFormControlInput1" placeholder="Contoh: andrewjustin31@mail.com" required>
                        <small id="error-email" class="form-text text-muted" style="color: red !important" v-if="errorEmail">{{ errorEmail }}</small>
                    </div>
                    <div class="form-group">    
                        <label for="phone">
                            No. Telp
                        </label>
                        <input v-model="phone" @keypress="handleKeypress('phone')" type="number" class="form-control" id="phone" placeholder="Contoh: 0822 5950 8497">
                        <small id="error-phone" class="form-text text-muted" style="color: red !important" v-if="errorPhone">{{ errorPhone }}</small>
                    </div>
                    <div class="form-group">
                        <label for="username">
                            Username
                        </label>
                        <input v-model="username" @keypress="handleKeypress('username')" type="text" class="form-control" id="username" placeholder="Contoh: andrewjstn" maxlength="10">
                        <small id="error-username" class="form-text text-muted" style="color: red !important" v-if="errorUsername">{{ errorUsername }}</small>
                    </div>
                    <div class="form-group">
                        <label for="exampleInputPassword1">
                            Password
                        </label>
                        <input v-model="password" @keypress="handleKeypress('password')" type="password" class="form-control" id="exampleInputPassword1" placeholder="*******" maxlength="7">
                        <small id="error-password" class="form-text text-muted" style="color: red !important" v-if="errorPassword">{{ errorPassword }}</small>
                    </div>
                    <div class="button-section">
                        <div class="button-submit">
                            <button @click.prevent="clickDaftar" type="button" class="btn btn-primary" data-dismiss="button" aria-label="button">
                                Daftar
                            </button>
                        </div>
                        <div class="button-reset">
                            <button @click="clickReset" type="button" class="btn btn-danger" data-dismiss="button" aria-label="button">
                                Reset
                            </button>
                        </div>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            name: '',
            gender: '',
            hobby: '',
            email: '',
            phone: '',
            username: '',
            password: '',
            errorName: '',
            errorGender: '',
            errorHobby: '',
            errorEmail: '',
            errorPhone: '',
            errorUsername: '',
            errorPassword: '',
            hobby: [],
        }
    },
    watch: {
      gender() {
        if (this.gender) this.errorGender = ''
      },
      hobby() {
        if (this.hobby) this.errorHobby = '' 
      }
    },
    methods: {
        validateInput() {
            if (this.name == '') {
                this.errorName = 'Nama harus di isi!'
                this.showAlert('Field nama tidak boleh kosong!')
                return 
            }
            if (this.gender == '') {
                this.errorGender = 'Jenis kelamin harus di isi!'
                this.showAlert('Jenis kelamin harus di pilih!')
                return
            }
            if (this.hobby == '') {
                this.errorHobby = 'Hobby harus di isi!'
                this.showAlert('Hobby harus di pilih!')
                return
            }
            if (this.email == '') {
                this.errorEmail = 'Email harus di isi!'
                this.showAlert('Field email tidak boleh kosong!')
                return
            }
            if (this.phone == '') {
                this.errorPhone = 'No. Telp harus di isi!'
                this.showAlert('Field No. Telp tidak boleh kosong!')
                return
            }
            if (this.username == '') {
                this.errorUsername = 'Username harus di isi!'
                this.showAlert('Field Username tidak boleh kosong!')
                return
            }
            if (this.password == '') {
                this.errorPassword = 'Password harus di isi!'
                this.showAlert('Field password tidak boleh kosong!')
                return
            }
        },     
        showAlert(param) {
            alert(param)
        },
        handleKeypress(param) {
          if (param == 'name'){
            this.errorName = ''
          }
           if (param == 'gender'){
            this.errorGender = ''
          }
          if (param == 'hobby'){
            this.errorHobby = ''
          }
          if (param == 'email'){
            this.errorEmail = ''
          }
          if (param == 'phone'){
            this.errorPhone = ''
          }
          if (param == 'username'){
            this.errorUsername = ''
          }
          if (param == 'password'){
            this.errorPassword = ''
          }
        },
        clickDaftar() {
            this.validateInput()
            if (this.name && this.gender && this.hobby && this.email && this.phone && this.username && this.password) {
                this.showAlert('Anda berhasil mendaftar!')
            }
        },
        clickReset() {
            this.name = ''
            this.gender = ''
            this.hobby = ''
            this.email = ''
            this.phone = ''
            this.username = ''
            this.password = ''
        }        
    }
}
</script>

<style>
body {
  background-color: whitesmoke;
  font-family: nunito, sans-serif;
}
.coloum {
  padding-top: 20px;
  padding-bottom: 20px;
  background-color: white;
  box-shadow: 0 0 25px snow;
  font-size: 16px;
}
.name {
  font-style: italic;
  text-transform: capitalize;
}
.form-control {
  font-style: italic;
}
.button-section {
  display: flex;
  justify-content: space-around;
}
</style>