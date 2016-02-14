#flappy bird
#Author @Yuting

import pygame
from random import randint


black = (0,0,0)
white = (255,255,255)
blue = (37,241,245)
red = (255,0,0)
green = (0,255,0)

pygame.init()

pygame.display.set_caption("Flappy Bird")# set the name
size = 500,500
screen = pygame.display.set_mode(size)#set up the screen size


done = False

clock = pygame.time.Clock() #create a time tracker
sec = 60
clock.tick(sec)#get time every sec seconds

#draw the flappy heart
def tooth(x,y):
   pygame.draw.circle(screen,white,[x,y], 20)
#
#
def bar(xloc, yloc, xsize,ysize):
   pygame.draw.rect(screen, green, [xloc, yloc, xsize, ysize])#top bar
   pygame.draw.rect(screen, green, [xloc, int(yloc+ysize+space), xsize, ysize+500])#bot bar
def Score(score):
   font = pygame.font.Font(None ,50)
   text = font.render(("Score: "+str(score)), True, black)
   screen.blit(text, [0, 0])
#
def Start():
   font = pygame.font.Font(None ,30)
   text = font.render(("Press \"Space\" to Play the Game"), True, black)
   screen.blit(text, [0, 50])
   
def gameover ():
   font = pygame.font.SysFont(None, 60)
   text = font.render("Game over!", True, red)
   screen.blit(text, [150, 200])
   y_speed=0
   bar_speed = 0

 
x = 250
y = 250 
x_speed = 0
y_speed = 0
xloc = 500
xloc1 = xloc+250
yloc = 0
xsize = 80#wideth of the bar
space = randint(100,150)
bar_speed = 3
ysize = randint(0,250)
score = 0

#Begin the game
while not done:
   for event in pygame.event.get():

#quit      
      if event.type == pygame.QUIT:
            done = True
       
#press space, the heart will go up by 10            
      if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_SPACE:
               y_speed = -10
               
#release the space key, the heart will back down
      if event.type == pygame.KEYUP:
            if event.key == pygame.K_SPACE:
               y_speed = 5
#set up 
   screen.fill(blue)#set up the screen background
   tooth(x,y)#set the initial location of the heart: in the middel of the screen
   bar1=bar(xloc, yloc, xsize,ysize)
   bar2=bar(xloc1, yloc, xsize,ysize)
   Score(score)
   Start()
   
   y += y_speed#update the height of the heart
   xloc -= bar_speed#update the relative location of the bar
   xloc1 -= bar_speed
#Fail if the tooth touch the bottom
   if y > 690:
      gameover()
      bar_speed = 0
      y_speed = 0      
#Fail if the tooth touch the top
   if y < 10:
      gameover()
      bar_speed = 0
      y_speed = 0      
#Fail if the circle touch the 
   if x+20 > xloc and y-20 < ysize and x-15 < xsize + xloc:
      gameover()
      bar_speed = 0
      y_speed = 0
   if x+20 > xloc and y+20 > ysize+space and x-15 < xsize+xloc:
      gameover()
      bar_speed = 0
      y_speed = 0
   if x+20 > xloc1 and y-20 < ysize and x-15 < xsize + xloc+250:
         gameover()
         bar_speed = 0
         y_speed = 0
   if x+20 > xloc1 and y+20 > ysize+space and x-15 < xsize+xloc+250:
         gameover()
         bar_speed = 0
         y_speed = 0
#Make the bars moving 
   if xloc < 0:#determin the space between 2 bars
      xloc = 500#reset the location of the bar
   if xloc1< 0:
      xloc1 = 500
   
#calculate scores   
   if (x > xloc and x < xloc+3) or ((x > xloc1-3 and x < xloc1)):
      score = (score + 1)

      
   pygame.display.flip()


pygame.quit() #quit
