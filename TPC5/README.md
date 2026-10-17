# Trabalho para casa 4

# Autor:
Leonor Fernandes Coelho; ID: 113460; Foto: <img width="4032" height="3024" alt="image" src="https://github.com/user-attachments/assets/5e4edb18-fa38-4f3d-8f86-349d77b1ea93" />


# Resumo:
O trabalho de casa da quinta semana consistiu na implementação em Python de uma aplicação interativa para a gestão de alunos e turmas, estruturada através de um menu de operações.

A aplicação gere uma turma (representada como uma lista de alunos, em que cada aluno contém um nome, um ID e uma lista com três notas: TPC, projeto e teste). O programa permite criar uma turma nova, inserir novos alunos com notas geradas aleatoriamente, listar todos os elementos da turma e consultar um aluno específico através do seu ID. Além disso, a aplicação inclui funcionalidades de persistência de dados, permitindo guardar uma turma num ficheiro e carregar uma turma a partir de um ficheiro existente. Por fim, a opção de sair encerra o programa de forma segura.

## Jogo:
Disponibilizei o ficheiro na pasta TPC5, tal como o ficheiro turma criado por mim.

## Código:

import random

def criarTurma():
    return []

def inserirAluno(turma):
    nome = input("Indique o nome do aluno: ")
    id = input("Indique o id do aluno: ")
    notaTPC = random.randint(0, 20)
    notaProj = random.randint(0, 20)
    notaTeste = random.randint(0, 20)
    aluno = [nome, id, [notaTPC, notaProj, notaTeste]]
    turma.append(aluno)
    return aluno

def listarTurma(turma):
    if turma == []:
        print("A turma está vazia.")
    else:
        print("Turma atual:")
        for aluno in turma:
            print(f"- Nome: {aluno[0]}, ID: {aluno[1]}, Notas: {aluno[2]}")

def consultarAluno(turma):
    procurar = input("Indique o id que pretende procurar: ")
    encontrado = False
    for aluno in turma:
        if procurar == aluno[1]:
            print("Aluno encontrado: ", aluno)
            encontrado = True
    if not encontrado:
        print("id não encontrado.")

def guardarTurma(turma, fnome):
    if turma == []:
        print("A turma está vazia, nada para guardar.")
        return False
    
    file = open(fnome, "w", encoding="utf-8")
    res = ""
    for aluno in turma:
        nome = aluno[0]
        id = aluno[1]
        notas = aluno[2]
        res = res + nome + ";" + id + ";" + str(notas[0]) + ";" + str(notas[1]) + ";" + str(notas[2]) + "\n"
    
    file.write(res)
    file.close()
    return True

def carregarTurma(fnome):
    turma = []
    try:
        file = open(fnome, "r", encoding="utf-8")
        text = file.read()
        file.close()
        linhas = text.strip().split("\n")
        for linha in linhas:
            if linha:
                campos = linha.split(";")
                nome = campos[0]
                id = campos[1]
                notas = [int(campos[2]), int(campos[3]), int(campos[4])]
                turma.append([nome, id, notas])
        print("A turma foi carregada do ficheiro.")
    except FileNotFoundError:
        print("Ficheiro não encontrado. Certifique-se de que já guardou uma turma.")
    return turma

turma = []
n = ""
while n != "0":
    print("""
--- MENU DE GESTÃO DE ALUNOS ---
  (1) Criar uma turma;
  (2) Inserir um aluno na turma;
  (3) Listar a turma;
  (4) Consultar um aluno por id;
  (8) Guardar a turma em ficheiro;
  (9) Carregar uma turma dum ficheiro;
  (0) Sair da aplicação
""")

    n = input("Escolhe a opção pretendida: ")

    if n == "1":
        turma = criarTurma()
        print("Turma criada com sucesso!")
    elif n == "2":
        aluno = inserirAluno(turma)
        print("Aluno inserido: ", aluno)
    elif n == "3":
        listarTurma(turma)
    elif n == "4":
        consultarAluno(turma)
    elif n == "8":
        if guardarTurma(turma, "turma.txt"):
            print("O seu ficheiro foi criado com sucesso.")
    elif n == "9":
        turma = carregarTurma("turma.txt")
    elif n == "0":
        print("A sair da aplicação. Até breve!")
    else:
        print("A opção não é válida.")
