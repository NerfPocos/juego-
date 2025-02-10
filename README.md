import pygame as pg 
import sys 
from settings import * 
from map import *
from player import *
from raycasting import *


class Game: 
    def __init__(self):
        pg.init()
        self.screen=pg.display.set_mode(RES)
        self.clock = pg.time.Clock()
        self.delta_time = 1
        self.new_game()

    def new_game(self):
        self.map = Map(self)
        self.player = Player(self)
        self.raycasting = RayCasting(self)

    def update(self):
        self.player.update()
        self.raycasting.update()
        pg.display.flip()
        self.delta_time = self.clock.tick(FPS)
        pg.display.set_caption(f"{self.clock.get_fps():1f}")

    def draw(self):
        self.screen.fill('black')
        #self.map.draw()
        #self.player.draw()

    def check_events(self):
        for event in pg.event.get():
            if event.type == pg.QUIT or (event.type == pg.KEYDOWN and event.key == pg.K_ESCAPE):
                pg.quit()




import pygame as pg
from random import randint
from settings import *
_=False

randmap=randint(1,6)

if randmap==1:
    mini_map= [
        [1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
        [1,_,_,_,_,_,_,1,1,_,_,_,_,_,_,1],
        [1,_,1,1,1,_,_,_,_,_,_,_,1,1,_,1],
        [1,_,1,1,1,_,1,_,_,1,1,_,1,1,_,1],
        [1,_,1,_,_,_,1,1,_,_,_,_,_,_,_,1],
        [1,_,1,_,1,_,1,_,_,1,1,_,1,1,_,1],
        [1,_,1,_,1,_,_,_,_,_,1,_,1,1,_,1],
        [1,_,_,_,_,_,_,1,1,_,_,_,_,_,_,1],
        [1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
    ]

elif randmap==2:
    mini_map= [
        [1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
        [1,_,_,_,_,_,_,_,_,_,_,_,1,_,_,1],
        [1,_,1,1,_,_,_,1,1,_,_,_,1,1,_,1],
        [1,_,_,_,_,_,_,_,_,_,_,_,_,_,_,1],
        [1,1,1,_,_,_,1,1,1,1,1,_,_,1,1,1],
        [1,_,_,_,_,_,_,1,_,_,_,_,1,_,_,1],
        [1,_,_,_,_,_,_,1,1,_,_,1,1,_,_,1],
        [1,_,_,_,_,_,_,_,_,_,_,_,_,_,_,1],
        [1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
    ]

elif randmap==3:
    mini_map= [
        [1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
        [1,_,_,1,1,_,1,_,_,_,_,_,1,_,_,1],
        [1,_,_,1,_,_,_,1,_,_,1,_,1,1,_,1],
        [1,_,_,1,_,_,1,_,_,_,1,_,_,1,_,1],
        [1,_,_,1,_,1,1,_,1,_,1,_,_,1,_,1],
        [1,_,_,_,_,_,_,_,1,_,1,_,1,1,_,1],
        [1,_,_,_,1,_,1,_,1,_,1,_,_,1,_,1],
        [1,_,_,_,_,_,_,_,_,_,1,_,_,_,_,1],
        [1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
    ]

elif randmap==4:
    mini_map= [
        [1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
        [1,_,_,_,_,_,_,_,_,_,_,_,_,1,_,1],
        [1,_,1,_,_,1,1,1,1,_,1,_,_,1,_,1],
        [1,_,1,_,_,_,_,_,_,_,1,_,_,1,_,1],
        [1,_,1,1,_,1,1,1,1,1,1,_,_,1,_,1],
        [1,_,1,1,_,1,_,1,1,_,_,_,_,1,_,1],
        [1,_,1,_,_,_,_,_,1,_,1,_,_,1,_,1],
        [1,_,_,_,_,_,_,_,_,_,_,_,_,_,_,1],
        [1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
    ]

elif randmap==5:
    mini_map= [
        [1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
        [1,1,_,_,_,_,_,1,_,_,_,_,1,1,_,1],
        [1,_,_,_,1,_,_,1,_,1,_,_,_,_,_,1],
        [1,_,_,1,1,1,_,_,_,1,_,1,_,_,1,1],
        [1,_,_,_,1,1,1,1,1,1,1,1,1,_,_,1],
        [1,_,1,1,1,_,_,_,_,1,_,_,1,_,_,1],
        [1,_,_,_,1,_,1,_,1,1,_,_,_,_,1,1],
        [1,1,_,_,_,_,1,_,_,_,_,_,1,_,1,1],
        [1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
    ]

elif randmap==6:
    columnas=randint(100,200)
    filas=randint(70,170)
    #columnas=16
    #filas=9

    mini_map= []



    for i in range(filas):
        fila=[]
        for j in range(columnas):
            if i==0 or i==filas-1 or j ==0 or j == columnas-1:
                fila.append(1)

            else:
                pared=randint(1,6)

                if pared==1:
                    fila.append(1)

                else:
                    fila.append(0)

        mini_map.append(fila)


else:
    mini_map= [
        [1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
        [1,_,_,_,_,_,_,_,_,_,_,_,_,_,_,1],
        [1,_,_,1,1,1,1,_,_,_,1,1,1,_,_,1],
        [1,_,_,1,1,_,1,1,1,1,1,_,1,1,_,1],
        [1,_,_,_,_,_,1,_,_,_,1,_,_,_,_,1],
        [1,1,1,_,1,_,1,_,_,_,1,_,1,1,1,1],
        [1,_,1,_,1,_,1,_,1,_,_,_,_,_,_,1],
        [1,_,_,_,_,_,_,_,_,_,1,1,_,_,_,1],
        [1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
    ] 

class Map:
    def __init__(self,game):
        self.game = game
        self.mini_map=mini_map
        self.world_map={}


 from settings import *
import pygame as pg
import math

class Player:
    def __init__(self,game):
        self.game = game
        self.x , self.y =PLAYER_POS
        self.angle=PLAYER_ANGLE

    def movement (self):
        sin_a=math.sin(self.angle)
        cos_a=math.cos(self.angle)
        dx, dy = 0, 0
        speed=PLAYER_SPEED * self.game.delta_time

        speed_sin = speed * sin_a
        speed_cos = speed * cos_a

        keys = pg.key.get_pressed()

        if keys[pg.K_w]:
            dx += speed_cos
            dy += speed_sin

        if keys[pg.K_s]:
            dx += -speed_cos
            dy += -speed_sin

        if keys[pg.K_a]:
            dx += speed_sin
            dy += -speed_cos

        if keys[pg.K_d]:
            dx += -speed_sin
            dy += speed_cos

        self.check_wall_collision(dx,dy)

        if keys[pg.K_LEFT]:
            self.angle -=PLAYER_ROT_SPEED*self.game.delta_time

        if keys[pg.K_RIGHT]:
            self.angle +=PLAYER_ROT_SPEED*self.game.delta_time

        self.angle %=math.tau

    def check_wall(self,x,y):
        return (x,y) not in self.game.map.world_map

    def check_wall_collision(self,dx,dy):
        if self.check_wall(int(self.x+dx),int(self.y)):
            self.x += dx
        if self.check_wall(int(self.x),int(self.y+dy)):
            self.y += dy

    def draw(self):
       # pg.draw.line(self.game.screen,'yellow',(self.x * block, self.y * block), (self.x * block+WIDTH * math.cos(self.angle), self.y * block+WIDTH * math.sin(self.angle)),4)
        pg.draw.circle(self.game.screen,'green',(self.x * block, self.y * block),20*prop)

  

    import pygame as pg
import math
from settings import *

class RayCasting:
    def __init__(self,game):
        self.game=game
    
    def ray_cast(self):
        ox, oy = self.game.player.pos
        x_map,y_map=self.game.player.map_pos
        
        ray_angle=self.game.player.angle-HALF_FOV + 0.0001

        for ray in range(NUM_RAYS):
            sin_a= math.sin(ray_angle)
            cos_a= math.cos(ray_angle)

            x_vert,dx=(x_map +1,1) if cos_a > 0 else (x_map-1e-6, -1)

            depth_vert =(x_vert-ox)/cos_a
            y_vert = oy +depth_vert * sin_a

            delta_depth= dx / cos_a
            dy = delta_depth * sin_a

            for i in range (MAX_DEPTH):
                tile_vert= int(x_vert), int(y_vert)

                if tile_vert in self.game.map.world_map:
                    break

                x_vert+= dx
                y_vert+= dy
                depth_vert+= delta_depth

            y_hor, dy=(y_map+1,1) if sin_a >0 else (y_map -1e-6,-1)

            depth_hor=(y_hor-oy)/sin_a
            x_hor= ox +depth_hor * cos_a

            delta_depth= dy/sin_a
            dx=delta_depth * cos_a

            for i in range (MAX_DEPTH):
                tile_hor = int (x_hor), int(y_hor)
                if tile_hor in self.game.map.world_map:
                    break

                x_hor+=dx
                y_hor+=dy
                depth_hor+=delta_depth

            if depth_vert > depth_hor:
                depth=depth_hor

            else:
                depth=depth_vert

            #pg.draw.line(self.game.screen,"yellow",(ox*block,oy*block),(ox*block+depth*block*cos_a, oy*block+depth*block*sin_a),2)
            


            depth*=math.cos(self.game.player.angle - ray_angle)

    

    #game settings
import math

prop= 0.75
block=int(100*prop)
RES = WIDTH,HEIGHT = int(1600*prop),int(900*prop)
FPS = 60

HALF_WIDTH= WIDTH//2
HALF_HEIGHT= HEIGHT//2

PLAYER_POS =1.5, 5
PLAYER_ANGLE= 0
PLAYER_SPEED=0.004
PLAYER_ROT_SPEED=0.002

FOV= math.pi /3
HALF_FOV= FOV /2
NUM_RAYS=WIDTH // 2
HALF_NUM_RAYS= NUM_RAYS //2
DELTA_ANGLE= FOV / NUM_RAYS
MAX_DEPTH= 20

SCREEN_DIST= HALF_WIDTH / math.tan(HALF_FOV)
SCALE= WIDTH // NUM_RAYS

PLAYER_ROT_SPEED=0.002 
