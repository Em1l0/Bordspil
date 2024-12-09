from machine import Pin, SoftI2C, PWM
from I2C_LCD import I2cLcd
import random
from time import sleep_ms
leikur = True

p1hit = Pin(10, Pin.IN, Pin.PULL_UP)
p1stand = Pin(11, Pin.IN, Pin.PULL_UP)
p2hit = Pin(8, Pin.IN, Pin.PULL_UP)
p2stand = Pin(9, Pin.IN, Pin.PULL_UP)
p3hit = Pin(17, Pin.IN, Pin.PULL_UP)
p3stand = Pin(18, Pin.IN, Pin.PULL_UP)


p1blatt= Pin(15, Pin.OUT)
p1rautt= Pin(16, Pin.OUT)

p2blatt= Pin(6, Pin.OUT)
p2rautt= Pin(7, Pin.OUT)

p3rautt= Pin(5, Pin.OUT)
p3blatt= Pin(4, Pin.OUT)


i2c = SoftI2C(scl=Pin(13), sda=Pin(14), freq=400000)

passiveBuzzer = PWM(Pin(1), freq=1000)



passiveBuzzer.duty(0)




def stand():
    

    passiveBuzzer.duty(300)
    passiveBuzzer.freq(300)
    sleep_ms(120)
    passiveBuzzer.duty(200)
    sleep_ms(120)
    passiveBuzzer.duty(0)
    return




def hit():
    passiveBuzzer.freq(1000)
    tones = [220, 247, 392]
    for tone in tones:
        passiveBuzzer.duty(512)
        passiveBuzzer.freq(tone)
        sleep_ms(60)
    passiveBuzzer.duty(0)
    return


def loss():
        passiveBuzzer.duty(512)
        passiveBuzzer.freq(100)
        sleep_ms(20)
        passiveBuzzer.freq(120)
        sleep_ms(20)
        passiveBuzzer.freq(150)
        sleep_ms(300)
        passiveBuzzer.duty(0)
        sleep_ms(350)
        passiveBuzzer.duty(512)
        passiveBuzzer.freq(100)
        sleep_ms(20)
        passiveBuzzer.freq(120)
        sleep_ms(20)
        passiveBuzzer.freq(150)
        sleep_ms(600)
        passiveBuzzer.duty(0)



def victory():
    tones = [300, 350, 400, 450, 500] 
    for tone in tones:
        passiveBuzzer.duty(512)
        passiveBuzzer.freq(tone)
        sleep_ms(150)
    passiveBuzzer.duty(0)

skjarhus = I2cLcd(i2c, 34, 2, 16)




skjarhus.move_to(0, 0)

skjarhus.putstr("Hus")
skjarhus.move_to(0, 1)
skjarhus.putstr("")


skjar1 = I2cLcd(i2c, 36, 2, 16)

skjar2 = I2cLcd(i2c, 39, 2, 16)

skjar3 = I2cLcd(i2c, 32, 2, 16)

spilari1 = False
spilari2 = False
spilari3 = False


while True :
    skjarhus.move_to(0, 0)
    skjarhus.putstr("Hus")
    skjarhus.move_to(0, 1)
    skjarhus.putstr("")
    
    leikur = True
    
    spilastokkur = [11, 11, 11, 11, 2,2,2,2,3,3,3,3,4,4,4,4,5,5,5,5,6,6,6,6,7,7,7,7,8,8,8,8,9,9,9,9,10,10,10,10,'J','J','J','J','Q','Q','Q','Q','K','K','K','K',]
    gera = True
    spilari1spil = []
    spilari2spil = []
    spilari3spil = []
    #spilari1skjar= []
    #spilari2skjar= []
    #spilari3skjar = []
    husspil = []
    
    
    
    while leikur :
        spilari1 = False
        spilari2 = False
        spilari3 = False
        
        p1blatt(0)
        p1rautt(0)
        p2blatt(0)
        p2rautt(0)
        p3blatt(0)
        p3rautt(0)
        
        for i in range (6) :
            if p1hit.value()  == 0 or p1stand.value()  == 0 :
                spilari1 = True
                skjar1.move_to(0, 0)
                skjar1.putstr("spilari 1                       ")
                skjar1.move_to(0, 1)
                skjar1.putstr("")
                p1blatt(1)
                p1rautt(1)
                hit()
            if p2hit.value()  == 0 or p2stand.value()  == 0 :
                spilari2 = True
                skjar2.move_to(0, 0)
                skjar2.putstr("spilari 2                       ")
                skjar2.move_to(0, 1)
                skjar2.putstr("")
                p2blatt.value(1)
                p2rautt.value(1)
                hit()
            if p3hit.value()  == 0 or p3stand.value()  == 0 :
                spilari3 = True
                skjar3.move_to(0, 0)
                skjar3.putstr("spilari 3                       ")
                skjar3.move_to(0, 1)
                skjar3.putstr("")
                p3blatt.value(1)
                p3rautt.value(1)
                hit()
            sleep_ms (500)
            
        skjarhus.move_to(0, 1)
        skjarhus.putstr ('Leikur byrjar   ')
        
        for i in range (5) :
            passiveBuzzer.duty(250)
            if spilari1 :
                p1rautt.value(not p1rautt.value())
                p1blatt.value(not p1blatt.value())
            if spilari2 :
                p2rautt.value(not p2rautt.value())
                p2blatt.value(not p2blatt.value())
            if spilari3 :
                p3rautt.value(not p3rautt.value())
                p3blatt.value(not p3blatt.value())
            sleep_ms (150)
            passiveBuzzer.duty(200)
            sleep_ms(150)
        passiveBuzzer.duty(0)
        
        spil = random.choice(spilastokkur)
        if spil == 'Q' or spil == 'K' or spil == 'J' :
            husspil.append(10)
        else :
            husspil.append(spil)
        skjarhus.move_to(0, 1)
        skjarhus.putstr(str('               '))
        skjarhus.move_to(0, 1)
        skjarhus.putstr(str(spil))
        skjarhus.putstr(str(' '))
        sleep_ms(2000)
        spilari1loop = True
        
        
        p1rautt.value(0)
        p1blatt.value(0)
        p2rautt.value(0)
        p2blatt.value(0)
        p3rautt.value(0)
        p3blatt.value(0)
        
        if spilari1:
            p1rautt.value(1)
            p1blatt.value(1)
            while spilari1loop:
                
                
                sleep_ms(200)
                for i in spilari1spil :
                    if sum(spilari1spil) > 21 and i == 11 :
                        spilari1spil.remove(11)
                        spilari1spil.append(1)
                if p1stand.value() == 0 or sum(spilari1spil) > 21:  
                    spilari1loop = False
                    p1rautt.value(0)
                    p1blatt.value(0)
                    stand()
                elif p1hit.value() == 0:  
                    spil = random.choice(spilastokkur)
                    if spil == 11 :
                        skjar1.putstr('1')
                        skjar1.putstr(' ')
                    else :
                        skjar1.putstr(str(spil))
                        skjar1.putstr(str(' '))
                    hit()
                    if spil == 'Q' or spil == 'K' or spil == 'J': 
                        spilari1spil.append(10) 
                    else:
                        spilari1spil.append(spil)
                    sleep_ms(1000)  
                    
                    
        spilari2loop = True          
        if spilari2:
            p2rautt.value(1)
            p2blatt.value(1)
            while spilari2loop:
               
                sleep_ms(200)
                for i in spilari2spil :
                    if sum(spilari2spil) > 21 and i == 11 :
                        spilari2spil.remove(11)
                        spilari2spil.append(1)
                if p2stand.value() == 0 or sum(spilari2spil) > 21:
                    spilari2loop = False
                    p2rautt.value(0)
                    p2blatt.value(0)
                    stand()
                elif p2hit.value() == 0:
                    hit()
                    spil = random.choice(spilastokkur)
                    if spil == 11 :
                        skjar2.putstr('1')
                        skjar2.putstr(' ')
                    else :
                        skjar2.putstr(str(spil))
                        skjar2.putstr(str(' '))
                    if spil == 'Q' or spil == 'K' or spil == 'J':
                        spilari2spil.append(10)
                    else:
                        spilari2spil.append(spil)
                    sleep_ms(1000)
                 
        spilari3loop = True  
        if spilari3:
            p3rautt.value(1)
            p3blatt.value(1)
            while spilari3loop:
                 
                sleep_ms(200)
                for i in spilari3spil :
                    if sum(spilari3spil) > 21 and i == 11 :
                        spilari3spil.remove(11)
                        spilari3spil.append(1)
                if p3stand.value() == 0 or sum(spilari3spil) > 21:  
                    spilari3loop = False
                    p3rautt.value(0)
                    p3blatt.value(0)
                    stand()
                elif p3hit.value() == 0:
                    hit()
                    spil = random.choice(spilastokkur) 
                    if spil == 11 :
                        skjar3.putstr('1')
                        skjar3.putstr(' ')
                    else :
                        skjar3.putstr(str(spil))
                        skjar3.putstr(str(' '))
                    if spil == 'Q' or spil == 'K' or spil == 'J':  
                        spilari3spil.append(10)  
                    else:
                        spilari3spil.append(spil)  
                    sleep_ms(1000)  

        if spilari1 == False and spilari2 == False and spilari3 == False:
            leikur = False
        #skjarhus.putstr('                ')
        sleep_ms(1000)
        skjar1.move_to(0, 0)
        #skjarhus.putstr (str('                '))
        
        skjarhus.move_to(2, 1)
        while sum (husspil) <=17 :
            for i in husspil :
                    if sum(husspil) > 21 and i == 11 :
                        husspil.remove(11)
                        husspil.append(1)
                        
            spil = random.choice(spilastokkur)
            if spil == 'Q' or spil == 'K' or spil == 'J' :
                husspil.append(10)
            else :
                husspil.append(spil)
            if spil == 11 :
                skjarhus.putstr('1')
                skjarhus.putstr(' ')
            else :
                skjarhus.putstr(str(spil))
                skjarhus.putstr(str(' '))
            hit()
            sleep_ms (2000)
            if 11 in husspil and sum(husspil) > 21:
                        while 11 in husspil and sum(husspil) > 21:
                            husspil[husspil.index(11)] = 1
            # Check outcomes for each player, ensuring only one outcome per player
    if sum(spilari1spil) > 21:
        skjar1.move_to(0, 0)
        skjar1.putstr('spilari 1 tapadi')  # Player 1 busts
    elif sum(spilari1spil) == sum(husspil):
        skjar1.move_to(0, 0)
        skjar1.putstr('spilari 1 jafnt ')
    elif sum(spilari1spil) == 21 and sum(husspil) != 21:
        skjar1.move_to(0, 0)
        skjar1.putstr('spilari 1 vann ')
        victory()
    elif sum(husspil) > 21 or sum(spilari1spil) > sum(husspil):
        skjar1.move_to(0, 0)
        skjar1.putstr('spilari 1 vann ')
        victory()
    else:
        skjar1.move_to(0, 0)
        skjar1.putstr('spilari 1 tapadi')  # House wins

    if sum(spilari2spil) > 21:
        skjar2.move_to(0, 0)
        skjar2.putstr('spilari 2 tapadi')  # Player 2 busts
    elif sum(spilari2spil) == sum(husspil):
        skjar2.move_to(0, 0)
        skjar2.putstr('spilari 2 jafnt ')
    elif sum(spilari2spil) == 21 and sum(husspil) != 21:
        skjar2.move_to(0, 0)
        skjar2.putstr('spilari 2 vann ')
        victory()
    elif sum(husspil) > 21 or sum(spilari2spil) > sum(husspil):
        skjar2.move_to(0, 0)
        skjar2.putstr('spilari 2 vann ')
        victory()
    else:
        skjar2.move_to(0, 0)
        skjar2.putstr('spilari 2 tapadi')  # House wins

    if sum(spilari3spil) > 21:
        skjar3.move_to(0, 0)
        skjar3.putstr('spilari 3 tapadi')  # Player 3 busts
    elif sum(spilari3spil) == sum(husspil):
        skjar3.move_to(0, 0)
        skjar3.putstr('spilari 3 jafnt ')
    elif sum(spilari3spil) == 21 and sum(husspil) != 21:
        skjar3.move_to(0, 0)
        skjar3.putstr('spilari 3 vann ')
        victory()
    elif sum(husspil) > 21 or sum(spilari3spil) > sum(husspil):
        skjar3.move_to(0, 0)
        skjar3.putstr('spilari 3 vann ')
        victory()
    else:
        skjar3.move_to(0, 0)
        skjar3.putstr('spilari 3 tapadi')  # House wins

        
    
    skjarhus.move_to(0, 0)
    skjarhus.putstr("leikur buinn")
    skjarhus.move_to(0, 1)
    skjarhus.putstr("")        
    sleep_ms (5000) 
    skjar1.clear()
    skjar2.clear()
    skjar3.clear()
    skjarhus.clear()
    
    passiveBuzzer.duty(250)
    sleep_ms (400)
    passiveBuzzer.duty(250)
    sleep_ms (400)
    passiveBuzzer.duty(0)
