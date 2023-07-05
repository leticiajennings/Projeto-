# Projeto-


import csv

def adicionar_item():
    codigo = input("Digite o código do item: ")
    descricao = input("Digite a descrição do item: ")
    quantidade = input("Digite a quantidade disponível: ")
    
    with open("catalogo.csv", "a", newline="") as arquivo:
        writer = csv.writer(arquivo)
        writer.writerow([codigo, descricao, quantidade])
    
    print("Item adicionado com sucesso!")

def pesquisar_item():
    codigo = input("Digite o código do item: ")
    
    with open("catalogo.csv", "r") as arquivo:
        reader = csv.reader(arquivo)
        for linha in reader:
            if linha[0] == codigo:
                print("Descrição:", linha[1])
                print("Quantidade disponível:", linha[2])
                return
    
    print("Item não encontrado.")

def atualizar_quantidade():
    codigo = input("Digite o código do item: ")
    nova_quantidade = input("Digite a nova quantidade disponível: ")
    
    linhas_atualizadas = []
    
    with open("catalogo.csv", "r") as arquivo:
        reader = csv.reader(arquivo)
        for linha in reader:
            if linha[0] == codigo:
                linha[2] = nova_quantidade
            linhas_atualizadas.append(linha)
    
    with open("catalogo.csv", "w", newline="") as arquivo:
        writer = csv.writer(arquivo)
        writer.writerows(linhas_atualizadas)
    
    print("Quantidade atualizada com sucesso!")

def exibir_catalogo():
    with open("catalogo.csv", "r") as arquivo:
        reader = csv.reader(arquivo)
        for linha in reader:
            print("Código:", linha[0])
            print("Descrição:", linha[1])
            print("Quantidade disponível:", linha[2])
            print()
            
def menu():
    print("1. Adicionar item")
    print("2. Pesquisar item")
    print("3. Atualizar quantidade")
    print("4. Exibir catálogo")
    print("5. Sair")
    
    opcao = input("Digite a opção desejada: ")
    
    if opcao == "1":
        adicionar_item()
    elif opcao == "2":
        pesquisar_item()
    elif opcao == "3":
        atualizar_quantidade()
    elif opcao == "4":
        exibir_catalogo()
    elif opcao == "5":
        return
    else:
        print("Opção inválida. Tente novamente.")
    
    print()
    menu()

# Executa o programa 
menu()
