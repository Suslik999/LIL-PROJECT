import pygame
pygame.init()
win = pygame.display.set_mode((500,500))#РАЗМЕР ЭКРАНА
pygame.display.set_caption("Trump")#НАЗВАНИЕ

x = 50
y = 435
width = 40
height = 60
speed = 20#ЗАДАЛИ ВСЕ ПАРАМЕТРЫ
isJump=False
jumpCount=10

run=True
while run:
    pygame.time.delay(100)

    for event in pygame.event.get():
        if event.type==pygame.QUIT:
            run=False

    keys= pygame.key.get_pressed()#РЕАКЦИЯ НА НАЖАТИЕИ КЛАВИШ
    if keys[pygame.K_LEFT] and x>10:#поставилил границы(x>5)
        x-=speed
    if keys[pygame.K_RIGHT]and x<500-width-10:
        x+=speed
    if not(isJump):
        if keys[pygame.K_UP]and y>10:
            y-=speed
        if keys[pygame.K_DOWN]and y<500-height-20:
            y+=speed
        if keys[pygame.K_SPACE]:#Прыжок
            isJump=True
    else:
        if jumpCount>=-10:
            if jumpCount<0:
                y+= (jumpCount**2)/2
            else:
                y-= (jumpCount**2)/2
            jumpCount-=1#приземление
        else:
            isJump=False
            jumpCount=10

    win.fill((0,0,0))
    pygame.draw.rect(win,(224,108,117),(x,y,width,height))
    pygame.display.update()#обновление экрана
pygame.quit()
Антон лох
