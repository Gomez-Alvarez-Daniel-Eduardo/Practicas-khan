
var Beaver = function(x, y) {
    this.x = x;
    this.y = y;
    this.img = getImage("creatures/Hopper-Cool");
    this.sticks = 0;
};

Beaver.prototype.draw = function() {
    fill(240, 0, 0);
    this.y = constrain(this.y, 0, height-50);
    image(this.img, this.x, this.y, 40, 40);
};
// altere la velocidad de asenso y desenso de hopper de 5 a 8
// tambien cambie a protagonista de hopper a hoper cool
Beaver.prototype.hop = function() {
    this.img = getImage("creatures/Hopper-Cool") ;
    this.y -= 8;
};

Beaver.prototype.fall = function() {
    this.img = getImage("creatures/Hopper-Cool");
    this.y += 8;
};

Beaver.prototype.checkForStickGrab = function(stick) {
    if ((stick.x >= this.x && stick.x <= (this.x + 40)) &&
        (stick.y >= this.y && stick.y <= (this.y + 40))) {
        stick.y = -400;
        this.sticks++;
    }
};
// se agregan puntos negativos 
Beaver.prototype.checkForBadGrab = function(antiStick) {
    if ((antiStick.x >= this.x && antiStick.x <= (this.x+40)) &&(antiStick.y >= this.y &&antiStick.y <= (this.y+40))) {
        antiStick.y = -400;
        this.sticks--;
    }
};

var Stick = function(x, y) {
    this.x = x;
    this.y = y;
};

Stick.prototype.draw = function() {
    fill(27, 8, 245);
    rectMode(CENTER);
    rect(this.x, this.y, 5, 40);
};
// posicionamos los puntos negativos 
var antiStick = function(x, y) {
    this.x = x;
    this.y = y;
};
//draw de los puntos negativos
antiStick.prototype.draw = function() {
    fill(233, 245, 10);
    rectMode(CENTER);
    rect(this.x, this.y, 5, 40);
};

var beaver = new Beaver(200, 300);

var sticks = [];
for (var i = 0; i < 40; i++) {  
    sticks.push(new Stick(i * 40 + 300, random(20, 260)));
} 
// cantidad de los puntos negativos 
var antiSticks = [];
for (var i = 0; i < 40; i++) {
    antiSticks.push(new antiStick(i * 40 + 300, random(0,260)));
}

var grassXs = [];
for (var i = 0; i < 25; i++) { 
    grassXs.push(i*20);
}

draw = function() {
    
    // static
    background(227, 254, 255);
    fill(130, 79, 43);
    rectMode(CORNER);
    rect(0, height*0.90, width, height*0.10);
    
    for (var i = 0; i < grassXs.length; i++) {
        image(getImage("cute/GrassBlock"), grassXs[i], height*0.85, 20, 20);
        grassXs[i] -= 1;
        if (grassXs[i] <= -20) {
            grassXs[i] = width;
        }
    }
    
    for (var i = 0; i < sticks.length; i++) {
        sticks[i].draw();
        beaver.checkForStickGrab(sticks[i]);
        sticks[i].x -= 1;
    }
    // imprime en movimiento a los puntos negativos 
    for (var i =0; i < antiSticks.length; i++) {
        antiSticks[i].draw();
        beaver.checkForBadGrab(antiSticks[i]);
        antiSticks[i].x -= 1; 
    } 
    fill(255, 115, 76);
    textSize(18);
    text("Score: " + beaver.sticks, 20, 30);
    
    // instrucciones
    textSize(11);
    fill(24, 17, 120);    
    text("puntos azules dan 1 punto ", 10, 360); 
    fill(194, 214, 15);    
    text("puntos amarillos quitan 1 punto ", 10, 377); 
    fill(227, 154, 220);    
    text("Ganas si tienes 20 puntos al terminar el escenario ", 10, 396);     
    
    if (beaver.sticks/sticks.length >= 0.50) {
        textSize(36);
        //agregamos un color para el texto de victoria
        fill(204, 0, 255); 
        text("YOU WIN!!!!", 100, 200); 
    }
    
    if (keyIsPressed && keyCode === 0) {
        beaver.hop();
    } else {
        beaver.fall();
    }
    beaver.draw();
};
