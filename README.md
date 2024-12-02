# cadastro-de-clientes
sistema criado para cadastramento de contatos 
 # Bem-vindos à lista de contatos de Julia Fonseca
print("Bem-vindos à lista de contatos de Julia Fonseca")  # EXIGÊNCIA DE CÓDIGO 1 de 8

# Lista para armazenar os contatos
lista_contatos = []  # EXIGÊNCIA DE CÓDIGO 7 de 8

# Variável global para gerar os IDs
id_global = 12345678  # Coloque seu RU aqui [EXIGÊNCIA DE CÓDIGO 2 de 8]

# Função para cadastrar contatos
def cadastrar_contato(id_):
    nome = input("Informe o nome do contato: ")  # Pergunta o nome do contato [EXIGÊNCIA DE CÓDIGO 3a de 8]
    atividade = input("Informe a atividade: ")  # Pergunta a atividade
    telefone = input("Informe o telefone: ")  # Pergunta o telefone
    contato = {'id': id_, 'nome': nome, 'atividade': atividade, 'telefone': telefone}  # Armazena em um dicionário [EXIGÊNCIA DE CÓDIGO 3b de 8]
    lista_contatos.append(contato.copy())  # Adiciona à lista de contatos [EXIGÊNCIA DE CÓDIGO 3c de 8]

# Função para consultar contatos
def consultar_contatos():
    while True:
        opcao = input("Consultar (1-Todos / 2-Por Id / 3-Por Atividade / 4-Retornar): ")  # Pergunta qual opção deseja [EXIGÊNCIA DE CÓDIGO 4a de 8]
        if opcao == "1":  # Consultar todos [EXIGÊNCIA DE CÓDIGO 4ai de 8]
            for contato in lista_contatos:
                print(contato)
        elif opcao == "2":  # Consultar por Id [EXIGÊNCIA DE CÓDIGO 4aii de 8]
            try:
                id_pesquisa = int(input("Informe o id do contato: "))  # Certifique-se de que o ID é um número inteiro
                encontrado = False
                for contato in lista_contatos:
                    if contato['id'] == id_pesquisa:
                        print(contato)
                        encontrado = True
                        break
                if not encontrado:
                    print("Id não encontrado.")
            except ValueError:
                print("Entrada inválida. O ID deve ser um número inteiro.")
        elif opcao == "3":  # Consultar por Atividade [EXIGÊNCIA DE CÓDIGO 4aiii de 8]
            atividade_pesquisa = input("Informe a atividade: ")
            encontrado = False
            for contato in lista_contatos:
                if contato['atividade'] == atividade_pesquisa:
                    print(contato)
                    encontrado = True
            if not encontrado:
                print("Nenhum contato encontrado com essa atividade.")
        elif opcao == "4":  # Retornar ao menu [EXIGÊNCIA DE CÓDIGO 4aiv de 8]
            return
        else:
            print("Opção inválida.")  # Opção inválida [EXIGÊNCIA DE CÓDIGO 4av de 8]

# Função para remover contatos
def remover_contato():
    while True:
        try:
            id_remover = int(input("Informe o id do contato a ser removido: "))  # Pergunta o id do contato [EXIGÊNCIA DE CÓDIGO 5a de 8]
            removido = False
            for contato in lista_contatos:
                if contato['id'] == id_remover:
                    lista_contatos.remove(contato)  # Remove o contato da lista [EXIGÊNCIA DE CÓDIGO 5b de 8]
                    removido = True
                    print(f"Contato com id {id_remover} removido com sucesso.")
                    return
            if not removido:
                print("Id inválido.")  # Id inválido [EXIGÊNCIA DE CÓDIGO 5c de 8]
        except ValueError:
            print("Entrada inválida. Digite um número.")

# Menu principal [EXIGÊNCIA DE CÓDIGO 6 de 8]
while True:
    opcao = input("Menu (1-Cadastrar / 2-Consultar / 3-Remover / 4-Encerrar): ")  # Pergunta qual opção deseja [EXIGÊNCIA DE CÓDIGO 6a de 8]
    if opcao == "1":  # Cadastrar contato
        id_global += 1  # Incrementa o id_global [EXIGÊNCIA DE CÓDIGO 6ai de 8]
        cadastrar_contato(id_global)
    elif opcao == "2":  # Consultar contato
        consultar_contatos()
    elif opcao == "3":  # Remover contato
        remover_contato()
    elif opcao == "4":  # Encerrar programa
        print("Programa encerrado.")
        break  # Sai do loop [EXIGÊNCIA DE CÓDIGO 6aiv de 8]
    else:
        print("Opção inválida.")  # Opção inválida [EXIGÊNCIA DE CÓDIGO 6av de 8]
