<template>
  <div class="container">
    <h3>Form Verileriyle Çalışmak</h3>
    <hr>
    <div class="row">
      <div class="col-md-6" v-if="isSubmitted" >
        <div class="panel panel-warning">
          <div class="panel-heading">
            <h4>Başvuru Formu</h4>
          </div>
          <div class="panel-body">
            <form>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label for="email">Kullanıcı Adı</label>
                    <input  v-model.lazy="userData.username" type="text" id="username" class="form-control" >
                  </div>
                  <div class="form-group">
                    <label for="password">Şifre</label>
                    <input  v-model.lazy.trim="userData.password"  type="password" id="password" class="form-control">
                  </div>
                  <div class="form-group">
                    <label for="age">Yaş</label>
                    <input v-model.lazy.trim="userData.age" type="number" value="age" id="age" class="form-control">
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label for="message">Açıklama</label><br>
                  <textarea v-model.lazy="userData.message" id="message" rows="3" class="form-control"></textarea>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label>
                      <input v-model.lazy="userData.interests" type="checkbox" value="yazilim"> Yazılım
                    </label>
                    <label>
                      <input v-model.lazy="userData.interests" type="checkbox" value="donanim"> Donanım
                    </label>
                  </div>

                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label>
                    <input v-model="userData.gender" type="radio" value="erkek"> Erkek
                  </label>
                  <label>
                    <input v-model="userData.gender" type="radio" value="kadin"> Kadın
                  </label>
                </div>
              </div>
              <div class="row" >
                <div  class="col-md-12 from-group">
                  <label >Şehir</label>
                  <select v-model="userData.selectedCity"  class="form-control">
                    <option :selected = "city == 'İstanbul' " 
                    v-for="city in userData.cities" > {{city}}
                    </option>
                  </select>
                </div>
              </div>
              <hr>
              <div class="row">
                <div class="col-md-12">
                  <button 
                    @click.prevent="submit"
                    class="btn btn-primary">Gönder!
                  </button>
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
      <div class="col-md-6">
          <div class="panel panel-info">
            <div class="panel-heading">
              <h4>Form Verileri</h4>
            </div>
            <div class="panel-body">
              <p>Kullanıcı Adı: {{userData.username}} </p>
              <p>Şifre: {{userData.password}}</p>
              <p>Yaş: {{userData.age}}</p>
              <p>Açıklama: {{userData.message}} </p>
              <p><strong>İlgi Alanları {{userData.interests}}</strong></p>
              <ul>
                <li></li>
              </ul>
              <p>Cinsiyet: {{userData.gender}}</p>
              <p>Şehir: {{userData.selectedCity}}</p>
              <p>Toggle:</p>
            </div>
          </div>
      </div>
    </div>

  </div>
</template>

<script>
  export default {
     data(){
      return {
        userData : {
          username : '',
          password : '',
          age : '',
          message : '',
          interests : [ ],
          gender : '',
          cities : ['İzmir', 'İstanbul' , 'Ankara', 'Antalya'],
          selectedCity : ''
        },
        isSubmitted : false
      }
    },
    methods : {
      submit(){
        this.isSubmitted = true;  
      }
    }
  }
</script>

<style>

</style>
