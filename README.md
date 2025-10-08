# TPC-3
import random

def menu():
    print("Manipulação de Listas de Inteiros")
    print("(1) Criar Lista (aleatória)")
    print("(2) Ler Lista (do utilizador)")
    print("(3) Soma")
    print("(4) Média")
    print("(5) Maior")
    print("(6) Menor")
    print("(7) Ordem crescente")
    print("(8) Ordem decrescente")
    print("(9) Procura um elemento")
    print("(0) Sair")

def criar_lista_aleatoria(tamanho):
    if tamanho <= 0:
        return []
    lista = []
    i = 0
    while i < tamanho:
        lista.append(random.randint(1, 100))
        i += 1
    return lista

def ler_lista_utilizador(tamanho):
    lista = []
    i = 0
    while i < tamanho:
            valor = int(input(f"Introduz o elemento {i} (inteiro): "))
            lista.append(valor)
            i += 1
    else:
            print("Valor inválido. Introduz um inteiro.")
    return lista

def soma_lista(lista):
    if not lista:
        return 0
    total = 0
    i = 0
    while i < len(lista):
        total += lista[i]
        i += 1
    return total

def media_lista(lista):
    if not lista:
        return None
    total = soma_lista(lista)
    return total / len(lista)

def maior_elemento(lista):
    if not lista:
        return None
    maior = lista[0]
    i = 1
    while i < len(lista):
        if lista[i] > maior:
            maior = lista[i]
        i += 1
    return maior

def menor_elemento(lista):
    if not lista:
        return None
    menor = lista[0]
    i = 1
    while i < len(lista):
        if lista[i] < menor:
            menor = lista[i]
        i += 1
    return menor

def esta_ordenada_crescente(lista):
    if len(lista) < 2:
        return True
    i = 0
    while i < len(lista) - 1:
        if lista[i] > lista[i+1]:
            return False
        i += 1
    return True

def esta_ordenada_decrescente(lista):
    if len(lista) < 2:
        return True
    i = 0
    while i < len(lista) - 1:
        if lista[i] < lista[i+1]:
            return False
        i += 1
    return True

def procura_elemento(lista, valor):
    i = 0
    while i < len(lista):
        if lista[i] == valor:
            return i
        i += 1
    return -1

def main():
    lista_atual = []  # variável interna que guarda a lista
    while True:
        menu()
        opcao = input("Escolhe uma opção (número): ")
        if not opcao:
            print("Opção vazia. Tenta outra vez.") ##se não colocar nada na barra de resposta, aparece esta linha
            continue
        if opcao == "1":
                n = int(input("Quantos elementos queres gerar? "))
                if n < 0:
                      print("Resposta inválida. Tente outra vez.")
                if n >= 0:
                  lista_atual = criar_lista_aleatoria(n)
                  print("Nova lista (aleatória) criada:", lista_atual)
        elif opcao == "2":
                n = int(input("Quantos elementos vais introduzir? "))
                if n < 0:
                    print("Resposta inválida. Tente outra vez.")
                if n >= 0:
                  lista_atual = ler_lista_utilizador(n)
                  print("Nova lista (do utilizador) criada:", lista_atual)
        elif opcao == "3":
            if not lista_atual:
                print("Lista vazia — nada para somar.")
            else:
                s = soma_lista(lista_atual)
                print("Soma dos elementos:", s)
        elif opcao == "4":
            if not lista_atual:
                print("Lista vazia — média indefinida.")
            else:
                m = media_lista(lista_atual)
                print("Média dos elementos:", m)
        elif opcao == "5":
            if not lista_atual:
                print("Lista vazia — maior elemento indefinido.")
            else:
                mx = maior_elemento(lista_atual)
                print("Maior elemento:", mx)
        elif opcao == "6":
            if not lista_atual:
                print("Lista vazia — menor elemento indefinido.")
            else:
                mn = menor_elemento(lista_atual)
                print("Menor elemento:", mn)
        elif opcao == "7":
            if esta_ordenada_crescente(lista_atual):
                print("Sim — a lista está ordenada por ordem crescente.")
            else:
                print("Não — a lista NÃO está ordenada por ordem crescente.")
        elif opcao == "8":
            if esta_ordenada_decrescente(lista_atual):
                print("Sim — a lista está ordenada por ordem decrescente.")
            else:
                print("Não — a lista NÃO está ordenada por ordem decrescente.")
        elif opcao == "9":
            if not lista_atual:
                print("Lista vazia — nada para procurar.")
            else:
                  valor = int(input("Que valor queres procurar? "))
                  print("Valor não encontrado. Tente de novo.")
            if lista_atual:
                  valor = int(input("Que valor queres procurar? "))
                  pos = procura_elemento(lista_atual, valor)
                  print("Posição:", pos)
        elif opcao == "0":
            print("Programa terminado. Lista final guardada:", lista_atual)
            break
        else:
            print("Opção inválida. Tenta outra vez.")

if __name__ == "__main__":
    main()
