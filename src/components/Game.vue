<template>
<div>
    <img :src="Logo" width="800" height="280" class="img-fluid mx-auto">
    <p></p>
    <button v-on:click="randomHero" class="btn btn-secondary">Start</button><p></p>
    <button v-on:click="attack" class="btn btn-danger mb-4">Attack</button>
    <button v-on:click="special" class="btn btn-warning mb-4">SpecialAttack</button>
    <button class="btn btn-info mb-4" @click.prevent="playSound('https://x2convert.com/th/Thankyou?token=U2FsdGVkX19bZJxdoGOsoDtm%2bhSDT68ebxnJVQt%2fmC0uhrNShAX9So3QUa%2bR9%2fTlHliS8qMGDbVsQ%2bgeffrlSvLIKk1xhClamOJhCezP4%2b0%3d&s=youtube&id=&h=5900655569596403487')"><span class="fa fa-play-circle-o"></span>Music</button><p></p>
    <div class="contianer">
        <div class="row">
            <div class="col-4">
                Name : {{NameHero}}
                <br />
                <img :src="ImgHero" :height="HPHero" class="mx-auto" />
                <br>
                HP : {{HPHero}}
                <br>
                <img v-bind:style="{width : HPHero + 'px'}" :src="BloodHero" alt height="25px" class=" mx-auto" />
            </div>
            <div class="col-4">
                <img :src="ImgF" width="500" height="200" class="img-fluid mx-auto">
                <img :src="ImgWin" class="img-fluid mx-auto" width="500" height="200" />
                <img :src="ImgDraw" class="img-fluid mx-auto" width="500" height="200" />
                <img :src="ImgLose" class="img-fluid mx-auto" width="500" height="200" />
            </div>
            <div class="col-4">
                Name : {{NameMonster}}
                <br />
                <img :src="ImgMonster" :height="HPMonster" class="mx-auto" />
                <br>
                HP : {{HPMonster}}
                <br>
                <img v-bind:style="{width : HPMonster + 'px'}" :src="BloodMonster" alt height="25px" class=" mx-auto" />
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    data: function () {
        return {
            BloodHero: "https://cdn.discordapp.com/attachments/746260527235334237/748860632693997595/BloodHero.png",
            BloodMonster: "https://cdn.discordapp.com/attachments/746260527235334237/748860627560300544/BloodMonster.png",
            Hero: "",
            Monster: "",
            NameHero: "",
            NameMonster: "",
            HPHero: "",
            HPMonster: "",
            SPATKHero: "",
            SPATKMonster: "",
            ATKHero: "",
            ATKMonster: "",
            ImgWin: "https://cdn.discordapp.com/attachments/746260527235334237/748568823937892433/WIN0.png",
            ImgLose: "https://cdn.discordapp.com/attachments/746260527235334237/748568813561315328/LOSE0.png",
            ImgDraw: "https://cdn.discordapp.com/attachments/746260527235334237/748568804375920640/DRAW0.png",
            Logo: "https://cdn.freebiesupply.com/logos/large/2x/fighter-logo-png-transparent.png",
            Win: "https://cdn.discordapp.com/attachments/746260527235334237/748568823937892433/WIN0.png",
            Lose: "https://cdn.discordapp.com/attachments/746260527235334237/748568813561315328/LOSE0.png",
            Draw: "https://cdn.discordapp.com/attachments/746260527235334237/748568804375920640/DRAW0.png",
            ImgF: 'https://cdn.discordapp.com/attachments/746260527235334237/748568792455708872/FIGHT0.png',
            player: [{
                name: 'Wonder woman',
                hp: 800,
                image: 'https://i.pinimg.com/564x/ed/1f/4c/ed1f4c3e1c8f2793bc901539d3f81714.jpg'
            }, {
                name: 'Black Widow',
                hp: 700,
                image: 'https://i.pinimg.com/564x/5e/13/24/5e132461725bdaf8f61785abe25d5e93.jpg'
            }, {
                name: 'Captain Marvel',
                hp: 850,
                image: 'https://i.pinimg.com/564x/93/91/c0/9391c06539787a3493a2f4ee38acc1a2.jpg'
            }, {
                name: 'Captain America',
                hp: 875,
                image: 'https://i.pinimg.com/564x/00/ee/53/00ee530379caa64981dee7e5f510bc3a.jpg'
            }],
            monster: [{
                name: 'Thanos',
                hp: 850,
                image: 'https://i.pinimg.com/564x/22/2d/bc/222dbc927113d84e3ab5e94d066dff2a.jpg'
            }, {
                name: 'Hela',
                hp: 800,
                image: 'https://i.pinimg.com/564x/a6/5c/20/a65c209e48e7e7980429cf44e0932ca0.jpg'
            }, {
                name: 'Ultron',
                hp: 800,
                image: 'https://i.pinimg.com/564x/bc/b1/c9/bcb1c926197f92b5e2a4b8be0d44ca8b.jpg'
            }, {
                name: 'Loki',
                hp: 850,
                image: 'https://i.pinimg.com/564x/aa/d1/dc/aad1dc69b9e7c2d60321776ef757d511.jpg'
            }]
        }
    },
    methods: {
        randomHero: function () {
            this.Hero = Math.max(Math.floor(Math.random() * this.player.length));
            this.Monster = Math.max(Math.floor(Math.random() * this.monster.length));
            this.HPHero = this.player[this.Hero].hp
            this.HPMonster = this.monster[this.Monster].hp
            this.NameHero = this.player[this.Hero].name
            this.NameMonster = this.monster[this.Monster].name
            this.ImgHero = this.player[this.Hero].image
            this.ImgMonster = this.monster[this.Monster].image
            this.ImgWin = "";
            this.ImgLose = "";
            this.ImgDraw = "";
        },
        attack: function () {
            this.ATKHero = Math.max(Math.floor(Math.random() * 50) + 1, 10);
            this.ATKMonster = Math.max(Math.floor(Math.random() * 50) + 1, 10);
            if (this.HPHero != 0 && this.HPMonster != 0) {
                this.HPHero -= this.ATKMonster;
            }
            if (this.HPMonster != 0 && this.HPHero != 0) {
                this.HPMonster -= this.ATKHero;
            }
            if (this.HPMonster <= 0 & this.HPHero <= 0) {
                this.HPMonster = 0;
                this.HPHero = 0;
                this.ImgDraw = this.Draw;
            } else if (this.HPMonster <= 0) {
                this.HPMonster = 0;
                this.ImgWin = this.Win;
            } else if (this.HPHero <= 0) {
                this.HPHero = 0;
                this.ImgLose = this.Lose;
            }
        },
        special: function () {
            this.SPATKHero = Math.max(Math.floor(Math.random() * 100) + 1, 50);
            this.SPATKMonster = Math.max(Math.floor(Math.random() * 100) + 1, 50);
            if (this.HPHero != 0 && this.HPMonster != 0) {
                this.HPMonster -= this.SPATKHero;
            }
            if (this.HPHero != 0 && this.HPMonster != 0) {
                this.HPHero -= this.SPATKMonster;
            }
            if (this.HPMonster <= 0 & this.HPHero <= 0) {
                this.HPMonster = 0;
                this.HPHero = 0;
                this.ImgDraw = this.Draw;
            } else if (this.HPMonster <= 0) {
                this.HPMonster = 0;
                this.ImgWin = this.Win;
            } else if (this.HPHero <= 0) {
                this.HPHero = 0;
                this.ImgLose = this.Lose;
            }
        },
        playSound(sound) {
            if (sound) {
                var audio = new Audio(sound);
                audio.play();
            }
        }
    }
}
</script>


<style>
body {
    font-family: 'Russo One', sans-serif;
}
</style>