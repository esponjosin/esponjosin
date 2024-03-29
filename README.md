<p align="center" href="https://esponjosin.com">
    <img align="center" class="image" src="https://esponjosin.com/assets/img/avatar.gif" style="border-radius:60px;" width="120" height="120">
</p>

<p align="center" style="margin: 20px;">
    <a href="https://github.com/Esponjosin" alt="GitHub"><img style="width:20px;" src="https://cdn-icons-png.flaticon.com/512/25/25231.png"></a>
</p>

<details align="center">
    <p align="center">
    <img align="center" src="https://github-readme-stats.vercel.app/api?username=esponjosin&show_icons=true&theme=tokyonight" />
    </p>
</details>

<p align="center" style="margin: 20px;">My Code:</p>

```ts
import * as fs from 'fs';

import { Voice, Person, StyleCode, Postures, Posture } from './structures/Esponjosin';

import { FastFood } from './24Hours';
import { Food } from './supermarket';

export default class Esponjosin extends Person {

    private realname: string
    private internetname: string
    private age: number
    private sleeping: boolean

    constructor(realname: string, internetname: string, age: number) {
        
        this._realname = realname;
        this._internetname = internetname;
        this._age = age;
        this._sleeping = false;

    }

    public async Speak(text: string): Voice {
        return new Voice(text);
    }

    public async sleep(atHour: number): void {

        const isWeekend: boolean = ([0,6].indexOf(new Date().getDay()) != -1);

        if(this.isTimeToSleep(atHour, !isWeekend) && !this.sleeping) {

            this.sleeping = true;

            setTimeout(function () {
                this.sleepig = false;
                this.Speak('Good Morning!');
            }, 7200000)

        }

    }

    public async normalEat(food: Food): Voice {
        
        var belly: Food[] = [];
        
        belly.push(food);
        
        return this.Speak('Tabemono o arigatō');

    }

    public async fastEat(food: FastFood): Voice {
        
        var belly: FastFood[] = [];
        
        belly.push(food);
        
        return this.Speak('It was delicious!');

    }

    public async party(): boolean {

        if(this.sleeping) return false;

        const isWeekend: boolean = ([0,6].indexOf(new Date().getDay()) != -1);

        if(isWeekend && this.friendsNear.length > 5 && this.location == 'disco') {
            return this.startDance(Postures.random());
        }

    }

    private isTimeToSleep(atHour: number, atMorning: boolean): boolean {

        let argTime: string = new Date().toLocaleString("en-US", { timeZone: 'America/Argentina/Cordoba' });

        let hour: string = argTime.split(' ')[1].split(':')[0];

        let isMorning: boolean = argTime.includes('AM');

        return atMorning ? isMorning ? hour == atHour : false : !atMorning && !isMorning && hour == atHour;

    }

    private async code(inFile: string): string {
        
        let code = new StyleCode();

        fs.writeFileSync(inFile, code);
        
        return code;

    }

    public async die(atAge: number): void {
        console.log(`Esponjosin has died at ${atAge} years old`)
        return process.exit(0)
    }

}

```

<p align ="center" style="margin: 20px;"><img src="https://komarev.com/ghpvc/?username=esponjosin&style=flat-square&label=Hyper+super+duper+ultra+deluxe+mega+tera+giga+penta+hexa+zetta+yotta+counter"></p>
