Título: Trabalho para casa 1

Autor: Leonor Fernandes Coelho; ID: 113460; Foto: 

Resumo: 

O trabalho de casa da segunda semana consistiu na implementação de um jogo em Python denominado “Adivinha o número”. O programa tinha de incluir duas modalidades: na primeira, o computador escolher aleatoriamente um número entre 0 e 100 e o utilizador tenta adivinhá-lo; na segunda, é o utilizador que pensa num número e o computador tenta descobri-lo.

Em ambas as modalidades, quem tenta adivinhar deve responder utilizando apenas as opções “certo”, “maior” ou “menor”. Quando o número é finalmente identificado, o programa deve terminar indicando o número correto e o número total de tentativas necessárias para chegar ao resultado.

Para desenvolver o trabalho, implementei inicialmente cada modalidade em separado, garantindo que ambas funcionavam corretamente. Posteriormente, integrei as duas versões num único programa, adicionando um menu inicial que permite ao utilizador escolher qual das modalidades pretende jogar.

# Modalidade 1:computador pensa num número (entre 0 e 100), utilizador tenta adivinhar

import random

num = random.randint(0,100)
tentativas = 0
palpite = int(input("Qual achas que é o número?"))

while palpite != num:
    tentativas = tentativas + 1

    if palpite < num:
        print(f"O número é MAIOR que {palpite}!")
    elif palpite > num:
        print(f"O número é MENOR que {palpite}!")
    
    palpite= int(input("Tenta outra vez:"))

print (f"Acertaste! O número é {num}!")
tentativas = tentativas + 1
print(f"Usaste {tentativas} tentativas.")


# Modalidade 2: o utilizador pensa num número entre (0 e 100) e o computador tenta adivinhar.

#intervalo de números
sup = 100
inf = 0

# variável do número adivinhado
x = 0

# número de tentativas
testes = 0

pergunta = str()
certo = "certo"
while pergunta != certo:
    testes = testes + 1
    x= int((sup+inf) / 2)
    pergunta= input("O seu número é " + str(x) + "?")        
    if pergunta == "maior":
        inf = x
    else:
        sup = x
    
print("O número pensado é " + str (x) + " e o computador advinhou o número em " + str(testes) + " tentativas!")    

# Modalidade 1 + 2: O jogo pode ter 2 modalidades: computador pensa num número (entre 0 e 100), utilizador tenta adivinhar; ou, o utilizador pensa num número (entre 0 e 100) e o computador tenta adivinhar.

print("O jogo consiste em a pessoa adivinhar o número que o computador está a pensar e dizer em quantas tentativas tal se sucedeu, e vice-versa.")
print(" Apenas podes responder às perguntas do computador com maior, menor ou certo.")
ordem=input("Pretende: 1-pensar no número ou 2-adivinhar?")


sup = 100
inf = 0
x = 0
testes = 0

if ordem== "pensar" or ordem== "1":
    pergunta= str()
    certo= "certo"
    while pergunta!= certo:
        testes = testes + 1
        x= int((sup+inf) / 2)
        pergunta= input("O seu número é " + str(x) + "?")
        
        if pergunta == "maior":
            inf = x
        else:
            sup = x

    print("O número pensado é " + str (x) + " e o computador advinhou o número em " + str(testes) + " tentativas")    

elif ordem== "adivinhar" or ordem== "2":
    import random
    num = random.randint(0,100)
    tentativas = 0
    palpite = int(input("Qual achas que é o número?"))

    while palpite != num:
        tentativas = tentativas + 1

        if palpite < num:
            print(f"O número é MAIOR que {palpite}!")
        elif palpite > num:
            print(f"O número é MENOR que {palpite}!")
        palpite= int(input("Tenta outra vez:"))

    print (f"Acertaste! O número é {num} e adivinhaste o número em {tentativas} tentativas!")

