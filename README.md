
var monkey , monkey_running;
var banana ,bananaImage, obstacle, obstacleImage;
var FoodGroup, obstacleGroup;
var survivalTime=0;
var score;

function preload(){
  
  
  monkey_running =            loadAnimation("sprite_0.png","sprite_1.png","sprite_2.png","sprite_3.png","sprite_4.png","sprite_5.png","sprite_6.png","sprite_7.png","sprite_8.png")
  
  bananaImage = loadImage("banana.png");
  obstacleImage = loadImage("obstacle.png");
 
}



function setup() {
  createCanvas(400,400);
  
  monkey=createSprite(80,315,20,20);
  monkey.addAnimation("moving",monkey_running);
  monkey.scale=0.1;
  
  ground=createSprite(400,350,900,10);
  ground.x=ground.width/2;
  ground.velocityX=-4;
  console.log(ground.x);
  
  
  

  
}


function draw() {
  background(225);
  
  if(ground.x < 0){
    ground.x=ground.width/2;
  }
  
if(keyDown("space")){
  monkey.velocityY=-12;
}
  monkey.velocityY=monkey.velocityY+0.8;
  monkey.collide(ground);
  
  banana();
  obstacle();
  
  

  drawSprites();
}

function banana(){
  if(World.frameCount%80===0){
        banana=Math.round(random(120,120));
    var banana=createSprite(100,100,30,30);
    banana.addImage(bananaImage);
    banana.velocityX=-4;
    banana.scale=0.1;
    banana.lifetime=300;
  }
}

function obstacle(){
  if(World.frameCount%300===0){
    obstacle=Math.round(random(120,200))
    var obstacle=createSprite(200,330,10,10);
    obstacle.addImage(obstacleImage);
    obstacle.velocityX=-2;
    obstacle.scale=0.1;
    obstacle.lifetime=200;
  }
}













