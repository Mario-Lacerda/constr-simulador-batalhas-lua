# Desafio Dio - Construindo um Simulador de Batalhas com Lua



### **Projeto em Lua: Simulador de Batalhas**

lua

```lua
-- Classe Guerreiro
local Guerreiro = {}

function Guerreiro:__init(self, nome, forca, defesa)
  self.nome = nome
  self.forca = forca
  self.defesa = defesa
end

function Guerreiro:atacar(self, alvo)
  local dano = self.forca - alvo.defesa
  if dano > 0 then
    alvo.vida = alvo.vida - dano
    print(self.nome .. " atacou " .. alvo.nome .. " causando " .. dano .. " de dano.")
  else
    print(self.nome .. " atacou " .. alvo.nome .. ", mas o ataque foi bloqueado.")
  end
end

-- Classe Mago
local Mago = {}

function Mago:__init(self, nome, forca, defesa, mana)
  Guerreiro:__init(self, nome, forca, defesa)  -- Chama o construtor da classe pai
  self.mana = mana
end

function Mago:lancarMagia(self, alvo)
  if self.mana >= 10 then
    local dano = self.forca * 2
    alvo.vida = alvo.vida - dano
    self.mana = self.mana - 10
    print(self.nome .. " lançou magia em " .. alvo.nome .. " causando " .. dano .. " de dano.")
  else
    print(self.nome .. " tentou lançar magia, mas não tinha mana suficiente.")
  end
end

-- Classe Curandeiro
local Curandeiro = {}

function Curandeiro:__init__(self, nome, forca, defesa, cura)
  Guerreiro:__init(self, nome, forca, defesa)  -- Chama o construtor da classe pai
  self.cura = cura
end

function Curandeiro:curar(self, alvo)
  if self.cura >= 10 then
    alvo.vida = alvo.vida + self.cura
    self.cura = self.cura - 10
    print(self.nome .. " curou " .. alvo.nome .. " restaurando " .. self.cura .. " de vida.")
  else
    print(self.nome .. " tentou curar, mas não tinha cura suficiente.")
  end
end

-- Função principal
function main()
  -- Cria guerreiros
  local guerreiro1 = Guerreiro("Guerreiro 1", 10, 5)
  local guerreiro2 = Guerreiro("Guerreiro 2", 12, 6)

  -- Cria magos
  local mago1 = Mago("Mago 1", 8, 4, 20)
  local mago2 = Mago("Mago 2", 10, 5, 25)

  -- Cria curandeiros
  local curandeiro1 = Curandeiro("Curandeiro 1", 5, 3, 20)
  local curandeiro2 = Curandeiro("Curandeiro 2", 6, 4, 25)

  -- Simula a batalha
  while guerreiro1.vida > 0 and guerreiro2.vida > 0 do
    -- Guerreiro 1 ataca Guerreiro 2
    guerreiro1:atacar(guerreiro2)

    -- Mago 1 lança magia em Guerreiro 2
    mago1:lancarMagia(guerreiro2)

    -- Curandeiro 1 cura Guerreiro 1
    curandeiro1:curar(guerreiro1)

    -- Guerreiro 2 ataca Guerreiro 1
    guerreiro2:atacar(guerreiro1)

    -- Mago 2 lança magia em Guerreiro 1
    mago2:lancarMagia(guerreiro1)

    -- Curandeiro 2 cura Guerreiro 2
    curandeiro2:curar(guerreiro2)
  end

  -- Verifica o vencedor
  if guerreiro1.vida <= 0 then
    print("Guerreiro 2 venceu!")
  else
    print("Guerreiro 1 venceu!")
  end
end

main()
```



#### **Explicação:**



- O projeto define três classes: **Guerreiro**, **Mago** e **Curandeiro**. Cada classe tem seus próprios atributos e métodos.

  

- A função `main` cria objetos das três classes e simula uma batalha entre eles.

  

- Durante a batalha, os guerreiros atacam uns aos outros, os magos lançam magias e os curandeiros curam aliados.

  

- A batalha continua até que um dos guerreiros tenha sua vida reduzida a zero.

  

- O vencedor da batalha é impresso na tela.





  Agradecimento Especial autor e apoio:

o gênio experiente dinossauro super habilidoso,

https://github.com/VagnerBellacosa

