---
title: "Como utilizar a herança em Python"
url: "como-utilizar-a-heranca-em-python"
date: 2019-01-31T00:14:11-03:00
draft: false
descricao: "Nesse post de 5 minutos de leitura sobre como utilizar a Herança em Python você irá entender porque a herança é importante para o reaproveitamento de código"

tags: ["Python","Programação Orientada ao Objeto"]
tags_seo: "Como utilizar a herança em Python"
---

Nesse post, de leitura fácil e de 5 minutos, você irá entender como utilizar a Herança em Python assim como todos os seus jargões.A Herança em Python é super importante para reaproveitamento de códigos. Sendo assim, venha entender como usar esse recurso para potencializar seus projetos.

Principal mecanismo da herança
O principal mecanismo do recurso da herança é permitir que uma classe possa ser derivada de uma classe base, permitindo que um comportamento mais especifico seja implementado na subclasse. A herança, é também uma importante característica para ao reuso de algoritmos e evitar códigos redundantes que possam tornar difícil a manutenção da base de códigos.

# DANGER! Jargoens da herança!
Mas antes de nos aprofundar mais vamos discutir, revisar, um pouco sobre nomenclaturas e jargões. Quando uma classe “B” herda aspectos da classe “A” :

- a classe “B” é uma subclasse da classe “A”; .
- a clase “A” é uma super classe da classe “B”;
- a classe “B” é uma classe filha da classe “A”;
- a classe “A” é uma classe pai da classe “B”
- a classe “A” é a classe base
- a classe “B” é a classe derivada
- a classe “B” “…é uma…” classe “A”;
- Como utilizar a herança em Python

![Fig. 1: Jargoes do recurso da herança do Python](Jargoes-Heranca-Orientaçao-Objeto-Python.png)

Fig. 1: Jargoes do recurso da herança do Python

Como utilizar a herança em Python
Para exemplificar o mecanismo da herança, criamos uma classe Carro , código 1, que possui dois métodos: o inicializador (__init__) e o para escrever o tipo de motor que tem o carro (getMotor). Em seguida, criamos uma classe Taxi que irá apenas acessar, de duas formas diferentes, os métodos implementados em sua classe pai, Carro . Por fim , iremos instanciar um objeto da classe Taxi . O primeiro método de acesso é usando nome da classe em seguida o operador ponto ( . ) e por fim o nome do método. O segundo método de acesso é o acesso normal, objeto self, operador ponto (.) e por fim o nome do método.

```py
# Código 1 - Utilizando o recurso de herança
class Carro():
    def __init__(self):
        print("Criou um carro")
 
    def getMotor(self):
        print("tenho um motor a combustao")
 
class Taxi(Carro):
    def __init__(self):
        Carro.__init__(self)
        # Criou um carro
        self.getMotor()
 
car = Taxi()
# Criou um carro
# Tenho um motor a combustão
```

O resultado, no prompt de comando, foi primeiro a frase “Criou um carro” e em seguida a frase “Tenho um carro a combustão”. Os dois métodos de acesso invocaram os métodos implementados na classe Carro. O primeiro método acessa explicitamente o método da classe pai e o segundo método consegue demonstrar que os método implementados na classe pai, agora fazem parte da classe filha também. Quando uma classe herda outra classe, automaticamente ela pega todos os métodos e atributo da classe origina [4]. Caso você esteja com dificuldades de entender o código 1 revise a aulasobre como criar uma classe em Python. ”.

Como utilizar o recurso da herança em Python
Além disso, a classe derivada pode adicionar novos métodos e atributos. No código 2 iremos implementar um novo método para pegar passageiros para a classe Taxi . Esse método não é comum a todos os carros de passeio. [4]

```py
# código 2 - Especializando a classe Taxi
class Taxi(Carro):
    def __init__(self):
        Carro.__init__(self)
        # Criou um carro
        self.getMotor()
        # tenho um motor a combustão
 
    def getPassageiro(self):
        print("pegou um novo passageiro")
 
car = Taxi()
# Criou um carro
# Tenho um motor a combustão
car.getPassageiro()
# Pegou um novo passageiro
```

Relação “…é um(a) ..”

No post sobre composição explicamos, em linhas gerais, a relação “…tem um…”, “…é parte de … ”. Por exemplo, uma classe que descreve um carro ira ter objetos referentes ao motor, pneus, parte elétrica. Porém, existe outro tipo importante de relação : “… é um(a)…” Por exemplo, um bolo de chocolate “… é um…” bolo, uma maça é uma fruta. Quando esse tipo de relação é detectado é necessário usar o recurso da Herança.

Método super, para acesso de métodos da classe pai
No código 1, quando criamos a classe Taxi , discutimos sobre 2 métodos de acesso a classe pai: o método que escreve o nome da classe (e.g., Carro.getMotor) e o método normal. Porém, o método 1 não é muito usado pois ele não desacopla a classe derivada da classe pai.[10] Geralmente o método usado para acesso a classe pai é através do método super() . Iremos, no código 3 implementar um classe CarroEletric que deriva a classe Carro e implementa um método usando essa forma de acesso.

```py
# código 3
class CarroEletric(Carro):
    def __init__(self):
        super().__init__()
        self.getMotor()
 
car =  CarroEletric()
# Criou um carro
# Tenho um motor a combustão

```


Ao rodar o código 2 o resultado é semelhante ao resultado do código 1. A diferença agora que o método super desacopla as duas classes. Porém, o carro elétrico não tem um motor a combustão, por isso é necessário sobrescrever métodos da classe Pai.

Sobrescrevendo métodos da classe Pai
O método getMotor() retorna o esperado, porém o carro elétrico possui um motor diferente. É possível sobrescrever qualquer método da classe pai que não se adeque a classe filha. Para fazer isso é necessário definir o método na classe derivada com o mesmo nome do método indesejavel. O Python irá desprezar o método da classe pai e irá só dar atenção ao método definido na classe filha.

```py
# código 4 Sobrescrevendo método
# da classe pai
class CarroEletric(Carro):
    def __init__(self):
        super().__init__()
        self.getMotor()
 
    def getMotor(self):
        print("tenho um motor elétrico")
 
car = CarroEletric()
# Criou um carro
# Tenho um motor elétrico
```

Agora, o resultado foi o esperado que o carro elétrico tem um motor elétrico.

# Como a herança organiza o código
Em conclusão, a herança permite reaproveitar códigos mesmo que a alguns métodos necessitem ser implementados levemente diferentes nas classe filhas. A classe Carro pode ser reaproveitada e expandida pela classe Taxi e pode ser reaproveita e modificada pela classe CarroEletric . Geralmente, algumas classe levam um grande período de tempo de testes e desenvolvimento. Poder, usar elas como base permite inclusive ter menor custo de desenvolvimento.

Nesse tutorial introduzimos o recurso da herança. No próximo iremos discutir um pouco sobre clases conctretas,abstratas e classes interfaces. Poste sua dúvida nos comentários. Para seguir as atualizações se inscreva no canal do youtube e nos siga no facebook. em @professormarcolan.

Como a herança organiza o código

# Referencias 
- [1] ZELLE, John M. Python programming: an introduction to computer science. Franklin, Beedle & Associates, Inc., 2004.
- [2] DOWNEY, Allen. Think Python. ” O’Reilly Media, Inc.”, 2012.
- [3] PILGRIM, Mark. Dive Into Python. Createspace, 2009.
- [4] MATTHES, Eric. Python crash course: a hands-on, project-based introduction to programming. No Starch Press, 2015.
- [5]Smallshire, Robert. Bingham, Austin. The Python Apprentice. Packt Publishing ,2017.
- [6]https://www.sololearn.com/Play/Python
- [7]https://stackoverflow.com/questions/1301346/what-is-the-meaning-of-a-single-and-a-double-underscore-before-an-object-name
- [8]https://www.python.org/dev/peps/pep-0008/#naming-conventions
- [9] Spronck, P. (2016). The Coder’s Apprentice: Learning Programming with Python 3.
- [10] https://pt.stackoverflow.com/questions/22452/como-se-usa-e-para-que-serve-o-super-em-classes-python
- https://docs.python.org/3/