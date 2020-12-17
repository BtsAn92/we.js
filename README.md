# we.js
// ==UserScript==
// @name         Well
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  try to take over the world!
// @author       You
// @match        https://yandex.ru/*
// @grant        none
// ==/UserScript==
let yandexInput = document.getElementsByName("text")[0];
let button = document.getElementsByClassName("button")[1];
if (button!=undefined){ 
    yandexInput.value = "Гобой"
    button.click();
}else{
    let links = document.links;
    for(let i=0; i<links.length; i++){
        let link = links[i]
        if(link.href.includes("xn----7sbab5aqcbiddtdj1e1g.xn--p1ai")){
        link.click();
        break;
        }
    }
}
