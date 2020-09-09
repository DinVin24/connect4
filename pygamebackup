import pygame

height = 6
width = 7

def drawtable():
    pygame.draw.rect(screen, (0, 0, 255), rect)
    centerx = 40
    centery = 560
    m = 0
    for j in range(6):
        n = 0
        for i in range(7):
            pygame.draw.circle(screen, (0, 0, 0), (centerx + n, centery - m), 30)
            n += 70
        m += 70
    pygame.display.update()

def clean_screen():
    pygame.draw.rect(screen, (0, 0, 0), (0, 0, 500, 170))
    pygame.display.update()

def checkclick():
    for event in pygame.event.get():
        if event.type == pygame.MOUSEBUTTONDOWN:
            return True
    return False

def checkpos():
    mousex, mousey = pygame.mouse.get_pos()
    n = 10
    m = 70
    for i in range(7):
        if mousex <= m and mousex >= n:
            x = i + 1
            return x
        n+=70
        m+=70
    return True

def columnchecking(n, tile):
    for x in range(width):
        for y in range(5, -1, -1):
            if n == x+1:
                if grid[y][x] == "-":
                    grid[y][x] = tile
                    if tile == "x":
                        pygame.draw.circle(screen, red, (40 + 70 * x, 560 - 70 * (5-y)), 30)
                        pygame.display.update()
                        return 0
                    elif tile == "o":
                        pygame.draw.circle(screen, yellow, (40 + 70 * x, 560 - 70 * (5-y)), 30)
                        pygame.display.update()
                        return 0
                    else:
                        print("yo i didn't find the circle you sent idk")

def wincheck(tile):
    #horizontal
    for y in range(height):
        for x in range(width-3):
            if grid[y][x] == tile and grid[y][x+1] == tile and grid[y][x+2] == tile and grid[y][x+3] == tile:
                return True
    #verical
    for x in range(width):
        for y in range(height-3):
            if grid[y][x] == tile and grid[y+1][x] == tile and grid[y+2][x] == tile and grid[y+3][x] == tile:
                return True

    #diagonal \ i think
    for y in range(height-3):
        for x in range(width-3):
            if grid[y][x] == tile and grid[y+1][x+1] == tile and grid[y+2][x+2] == tile and grid[y+3][x+3] == tile:
                return True

    #diagonal / i think
    for y in range(height-3):
        for x in range(3, width):
            if grid[y][x] == tile and grid[y+1][x-1] == tile and grid[y+2][x-2] == tile and grid[y+3][x-3] == tile:
                return True

    return False

def coverturn():
    pygame.draw.rect(screen, (0, 0, 0), (20, 20, 200, 50))
    pygame.display.update()

def title_screen():
    x1 = 115
    y1 = 60
    pygame.draw.rect(screen, (192, 192, 192), (x1, y1, 285, 100))
    pygame.draw.rect(screen, (0, 0, 0), (x1+30, y1+22, 92, 56))
    pygame.draw.rect(screen, (0, 0, 0), (x1+163, y1+22, 92, 56))
    cont1 = font2.render('PLAY', True, white)
    cont2 = font2.render('AGAIN', True, white)
    leave = font2.render('QUIT', True, white)
    screen.blit(cont1, (x1+47, 85))
    screen.blit(cont2, (x1+45,107))
    screen.blit(leave, (x1+190,97))
    pygame.display.update()
    while True:
        if checkclick():
            buttonx, buttony = pygame.mouse.get_pos()
            if buttonx >= x1+30 and buttonx <= x1+122 and buttony >= y1+22 and buttony <= y1+78:
                return True
            if buttonx >= x1+163 and buttonx <= x1+255 and buttony >= y1+22 and buttony <= y1+78:
                return False

screen = pygame.display.set_mode((500, 600))
pygame.display.set_caption('Connect Four')
icon = pygame.image.load('dots.png')
pygame.display.set_icon(icon)
screen.fill((0, 0, 0))
pygame.display.init()
running = True
rect = (0, 170, 500, 600)
red = (255, 0, 0)
yellow = (255, 255, 0)
white = (255, 255, 255)
pygame.font.init()
font = pygame.font.SysFont('Comic Sans MS', 24)
font2 = pygame.font.SysFont('Arial', 20)
p1win = font.render('PLAYER ONE WON!', True, red)
p1turn = font.render('P1 TURN:', True, red)
p2win = font.render('PLAYER TWO WON!', True, yellow)
p2turn = font.render('P2 TURN:', True, yellow)
while running:
    row1 = ["-", "-", "-", "-", "-", "-", "-"]
    row2 = ["-", "-", "-", "-", "-", "-", "-"]
    row3 = ["-", "-", "-", "-", "-", "-", "-"]
    row4 = ["-", "-", "-", "-", "-", "-", "-"]
    row5 = ["-", "-", "-", "-", "-", "-", "-"]
    row6 = ["-", "-", "-", "-", "-", "-", "-"]
    grid = [row1, row2, row3, row4, row5, row6]
    drawtable()
    playerone = True
    playertwo = True
    while True:
        while playerone:
            screen.blit(p1turn, (20, 20))
            pygame.display.update()
            if checkclick():
                p1 = checkpos()
                columnchecking(p1, "x")
                coverturn()
                break
        if wincheck("x"):
            print("P1 WON!")
            screen.blit(p1win, (145, 15))
            pygame.display.update()
            playerone = False
            playertwo = False
            running = title_screen()
            clean_screen()
            break

        while playertwo:
            screen.blit(p2turn, (20, 20))
            pygame.display.update()
            if checkclick():
                p2 = checkpos()
                columnchecking(p2, "o")
                coverturn()
                break
        if wincheck("o"):
            print("P2 WON!")
            screen.blit(p2win, (145, 15))
            pygame.display.update()
            playerone = False
            playertwo = False
            running = title_screen()
            clean_screen()
            break
