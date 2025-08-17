"""
Gerador de atributos para Old Dragon
- Estilos:
  1) Clássico  -> 3d6 para cada atributo
  2) Aventureiro-> 4d6, descarta o menor, soma os 3 maiores
  3) Heróico   -> valores fixos [15,14,13,12,10,8]
"""

import random

ATRIBUTOS = ["Força", "Destreza", "Constituicao", "Inteligencia", "Sabedoria", "Carisma"]

def roll_sides(n, slides=6):
    return [random.randint(1, slides) for _ in range(n)]
# Rolar 'n' dados de 6 faces e retornar a lista de resultados.

class DistribuirAtributos:
    
    @staticmethod
    
    def classico():
    # Para cada atributo rola-se 3d6 e soma.
    # Retorna lista de 6 valores.
        valores = []
        for _ in range(6):
            dados = roll_sides(3, 6)
            valores.append(sum(dados))
        return valores
    
    @staticmethod
    
    def Aventureiro():
        valores = []
        for _ in range(6):
            dados = roll_sides(4,6)
            dados.sort()
            # Descartar menor e somar 3 maior
            soma = sum(dados[1:])
            valores.append(soma)
        return valores
        
    @staticmethod
    
    def heroico(shuffle = True):
    #shuffle=True permite aleatorizar a atribuição.
        base = [15, 14, 13, 12, 10, 8]
        if shuffle:
            random.shuffle(base)
        return base.copy()
    

class Personagem:
    
    def __init__(self, nome: str, atributos_values: list):
        if len(atributos_values) != 6:
            raise ValueError
        self.nome = nome
        self.atributos = {attr: val for attr, val in zip(ATRIBUTOS, atributos_values)}
    
    def exibir_informacoes(self):
        print(f"Nome: {self.nome}")
        for attr in ATRIBUTOS:
            print(f"{attr:13}: {self.atributos[attr]}")
    
    def get_atributos(self):
        return self.atributos.copy()
        
def escolher_estilo():
    print("Escolha o estilo de distribuicao: ")
    print("1 - Classico")
    print("2 - Aventureiro")
    print("3 - Heroico")
    while True:
        escolha = input("Digite 1, 2 ou 3: ").strip()
        if escolha in("1", "2", "3"):
            return int(escolha)
        print("Opcao invalida, tente novamente")
        
def main():
    nome = input("Digite o nome do personagem: ").strip() or "Sem nome"
    
    estilo = escolher_estilo()
    
    if estilo == 1:
        valores = DistribuirAtributos.classico()
        estilo_nome = "Classico"
    elif estilo == 2:
        valores = DistribuirAtributos.Aventureiro()
        estilo_nome = "Aventureiro"
    else:
        resp = input("Deseja embaralhar os valores heroicos antes de atribuir? (s/n): ").strip().lower()
        shuffle = (resp == "s" or resp == "sim")
        valores = DistribuirAtributos.heroico(shuffle = shuffle)
        estilo_nome = "Heroico"
        
    personagem = Personagem(nome, valores)
    
    print(f"\nAtributos gerados: {estilo_nome}")
    personagem.exibir_informacoes()
    
if __name__ == "__main__":
    main()
