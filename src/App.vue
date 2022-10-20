<template>
<div class="container">
    <h3>Form Verileriyle Çalışmak</h3>
    <hr>
    <div class="row">
        <div class="col-md-6">
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
                                    <input v-model="userData.username" type="text" id="username" class="form-control">
                                </div>
                                <div class="form-group">
                                    <label for="password">Şifre</label>
                                    <input type="password" id="password" class="form-control" v-model.lazy.trim="userData.password">
                                    <!-- ⁡⁢⁣⁢𝗹𝗮𝘇𝘆 >> 𝗺𝗲𝘃𝗰𝘂𝘁 𝗶𝗻𝗽𝘂𝘁 𝗱𝗼𝗹𝘂𝗽 𝗯𝗮ş𝗸𝗮 𝗶𝗻𝗽𝘂𝘁𝗮 𝗴𝗲ç𝗶𝗻𝗰𝗲 𝗴ö𝘀𝘁𝗲𝗿𝗶𝗹𝗺𝗲𝘀𝗶 𝘀𝗮ğ𝗹ı𝘆𝗼
                                    𝘁𝗿𝗶𝗺 >> 𝗕𝗼ş𝗹𝘂𝗸 𝗼𝗹𝗺𝗮𝘀ı𝗻ı ö𝗻𝗹ü𝘆𝗼𝗿 ⁡ -->
                                </div>
                                <div class="form-group">
                                    <label for="age">Yaş</label>
                                    <input type="number" id="age" class="form-control" v-model.number.trim="userData.age">
                                </div>
                            </div>
                        </div>
                        <div class="row">
                            <div class="col-md-12 form-group">
                                <label for="message">Açıklama</label><br>
                                <textarea id="message" rows="3" class="form-control" v-model="userData.message"></textarea>
                            </div>
                        </div>
                        <div class="row">
                            <div class="col-md-12">
                                <div class="form-group">
                                    <label>
                                        <input v-model="userData.interest" type="checkbox" value="yazilim"> Yazılım
                                    </label>
                                    <label>
                                        <input v-model="userData.interest" type="checkbox" value="donanim"> Donanım
                                    </label>
                                </div>

                            </div>
                        </div>
                        <div class="row">
                            <div class="col-md-12 form-group">
                                <label>
                                    <input v-model="userData.gender" type="radio" value="Erkek"> Erkek
                                </label>
                                <label>
                                    <input v-model="userData.gender" type="radio" value="Kadin"> Kadın
                                </label>
                            </div>
                        </div>
                        <div class="row">
                            <div class="col-md-12 from-group">
                                <label>Şehir</label>
                                <select v-model="userData.selectedCity" class="form-control">
                                    <option :selected="city=='Erzurum'" v-for="city in userData.cities" :key="city.id"> {{city}}</option>
                                </select>
                            </div>
                        </div>
                        <hr>
                        <div class="row">
                            <div class="col-md-12">
                                <button @click.prevent="submit" class="btn btn-primary">Gönder!
                                </button>
                            </div>
                        </div>
                    </form>
                </div>
            </div>
        </div>
        <div class="col-md-6" v-if="isSubmitted">
            <div class="panel panel-info">
                <div class="panel-heading">
                    <h4>Form Verileri</h4>
                </div>
                <div class="panel-body">
                    <p>Kullanıcı Adı: {{userData.username}}</p>
                    <p>Şifre:{{userData.password}}</p>
                    <p>Yaş : {{userData.age}}</p>
                    <p style="white-space:pre;">Açıklama: {{userData.message}} </p>
                    <p><strong>İlgi Alanları</strong></p>
                    <ul>
                        <li v-for="item in userData.interest" :key="item.index"> {{item}}</li>
                    </ul>
                    <p>Cinsiyet: {{userData.gender}}</p>
                    <p>Şehir: {{userData.selectedCity}}</p>

                </div>
            </div>
        </div>
    </div>

</div>
</template>

<script>
export default {
    data() {
        return {
            userData: {
                username: '',
                password: '',
                age: null,
                message: '',
                interest: [],
                gender: '',
                cities: ["İstanbul", "Ankara", "İzmir", "Erzurum", "Malatya"],
                selectedCity: ''
            },
            isSubmitted:false

        }
    },
    methods: {
        submit() {
        this.isSubmitted=true
        }
    }
}
</script>

<style>

</style>
