#algoritmo do aviao
preco = 700
precos_pagos = []
faturamento = 0
m = 4 
n = 20 
cont_lugar = 0
num = ['[1]','[2]','[3]','[4]']
letras = ['A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T']
conversao_letras = [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20]
matriz = [[f'[□]' for i in range(n)]for j in range(m)]
print('\nBEM-VINDO À MOZAN TURISMO!!!\n\nCOMPRE SUAS PASSAGENS AQUI!!!\n')

# realizar as contas
def calculos():
    faturamento = 0
    for i in range(len(precos_pagos)):
        faturamento += precos_pagos[i]
    taxa_ocup = cont_lugar/(m*n) * 100
    print('\nNós da MOZAN TURISMO lhe desejamos uma ótima viagem!')
    print(f'\nO faturamento da empresa foi de {faturamento} reais.')
    print(f'\nA taxa de ocupaçâo do vôo foi de {taxa_ocup:.2f} por cento.')

#printar matriz aviao

def mostrarmatriz():
    print('[A]','[B]','[C]','[D]','[E]','[F]','[G]','[H]','[I]','[J]','[K]','[L]','[M]','[N]','[O]','[P]','[Q]','[R]','[S]','[T]')
    for i in range(m):
        for j in range(n):
            if i == 2 and j == 0: print('')
            print(matriz[i][j], end = ' ')
        print(num[i])

mostrarmatriz()
print('\n■ Comece nos informando alguns dados do passageiro.\n■ Lembrando que crianças (0 até 5 anos) e idosos (+ de 65 anos) pagam apenas metade do valor da passagem.')
assento_ocupado = True
idade_errada = True
letra_errada = True
assento_errado = True
rodando = True
while rodando:
    preco = 700
    idade_errada = True
    while idade_errada:
        try:
            idade = int(input('\nDigite a idade do passageiro: '))
            idade_errada = False
        except ValueError:
            print("\nCaractere inválido! Por favor, digite uma idade válida.")
    if idade < 5 or idade > 65:
       preco = 350
       print(f'\nOk, O preço da passagem será {preco:.1f} reais.')
    else:
        print(f'\nOk, O preço da passagem será {preco} reais.')
    precos_pagos.append(preco)
    assento_ocupado = True
    while assento_ocupado:
        letra_errada = True
        while letra_errada:
            y = input('\nDigite em qual letra voce quer o assento: ').upper()
            if y in letras:
                for i in range(20):
                    if y == letras[i]:
                        letras[i] == conversao_letras[i]
                        y = conversao_letras[i]
                        letra_errada = False
            else:
                print('\nO caractere selecionado é inválido. Escolha uma das letras que aparecem na interface.')      
        assento_errado = True
        while assento_errado:
            x = int(input('\nDigite em qual número voce quer o assento: '))
            if x in (1,2,3,4):
                assento_errado = False
            else:
                print('\nNúmero inválido. Escolha um número entre 1 e 4.')
        if matriz[x-1][y-1] == '[■]':
            print('\nCadeira ja selecionada! Escolha outro assento.\n')
            mostrarmatriz()
        else:
            assento_ocupado = False
    matriz[x-1][y-1] = '[■]'
    cont_lugar += 1
    if cont_lugar == m * n:
        print('\nTODOS ASSENTOS SELECIONADOS!! Programa encerrando...\n')
        mostrarmatriz()
        calculos()    
        rodando = False
        continue
    print()
    mostrarmatriz()
    pergunta = input('\nDeseja continuar comprando?\n\n(S)im ou (N)ao\n').upper()
    if pergunta == 'N' or cont_lugar == m* n:
        if cont_lugar < (m*n)/2:
            print('\nINFELIZMENTE, POR FALTA DE VENDAS, ESTE VÔO FOI CANCELADO.')
            rodando = False
        else:
            calculos()
            rodando = False
    else:
        print('\nOK, INFORME NOVAMENTE OS DADOS DO PASSAGEIRO\n')
        mostrarmatriz()
        continue






        

  

  
