# atividade-Zelma-MariaJos--Kalyane
imagem e som

import ddf.minim.signals.*;
import ddf.minim.*;
import ddf.minim.analysis.*;
import ddf.minim.effects.*;

Minim minim;
AudioPlayer sou; 

PImage fonte;     
PImage destino;  

void setup() {
  size(900, 900); 
  fonte = loadImage("turma -presencial.jpg");  
  destino = createImage(fonte.width, fonte.height, RGB);

  minim = new Minim(this);
  sou = minim.loadFile("SOJA - brothers and sisters.mp3");
  sou.loop();
}

void draw() { 

  if (mousePressed == true) {
    float threshold = 127;


    fonte.loadPixels();
    destino.loadPixels();


    for (int x = 0; x < fonte.width; x++) {

      for (int y = 0; y < fonte.height; y++ ) {

        int loc = x + y*fonte.width;


        if (brightness(fonte.pixels[loc]) > threshold) {
          destino.pixels[loc]  = color(255);  // alterando o pixel para Branco
        } else {
          destino.pixels[loc]  = color(0);    // alterando o pixel para Preto
        }
      }
    }


    destino.updatePixels();

    image(destino, 0, 0);
  } else {

    image(fonte, 0, 0);
  }
}

