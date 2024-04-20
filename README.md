# -
import pygame
win_width = 700
win_height = 500
window = pygame.display.set_mode((win_width,win_height))
pygame.display.set_caption("Доганялки")

FPS = pygame.time.Clock()
game = True
class Settings:
    def __init__(self,image,x,y,width,heigts):
        self.rect = pygame.Rect(x,y,width,heigts)
        self.image = pygame.image.load(image)
        self.image = pygame.transform.scale(self.image,(self.rect.width,self.rect.height))
    def draw(self):
        window.blit(self.image,(self.rect.x,self.rect.y))


class Player(Settings):
    def __init__(self,image,x,y,w,h,s):
        super().__init__(image,x,y,w,h)
        self.speed =s
    def move1(self):
        keys=pygame.key.get_pressed()
        if keys[pygame.K_UP]and  self.rect.y>0:
            self.rect.y-=self.speed
        if keys[pygame.K_DOWN]and self.rect.y<win_height-self.rect.height:
            self.rect.y+=self.speed
        if keys[pygame.K_LEFT]and self.rect.x>0:
            self.rect.x-=self.speed
        if keys[pygame.K_RIGHT]and self.rect.x<win_width-self.rect.width:
            self.rect.x+=self.speed


class Player2(Settings):
    def __init__(self,image,x,y,w,h,s):
        super().__init__(image,x,y,w,h)
        self.speed =s
    def move2(self):
        keys=pygame.key.get_pressed()
        if keys[pygame.K_w]and  self.rect.y>0:
            self.rect.y-=self.speed
        if keys[pygame.K_s]and self.rect.y<win_height-self.rect.height:
            self.rect.y+=self.speed
        if keys[pygame.K_a]and self.rect.x>0:
            self.rect.x-=self.speed
        if keys[pygame.K_d]and self.rect.x<win_width-self.rect.width:
            self.rect.x+=self.speed

p2 = Player2("sprite2.png",300,0,100,100,10)
p1=Player("sprite1.png",0,0,100,100,10)
back = Settings("background.png",0,0,win_width,win_height)
while game:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            game = False
    back.draw()
    p1.draw()
    p1.move1()
    p2.draw()
    p2.move2()
    pygame.display.update()
    FPS.tick(60)

