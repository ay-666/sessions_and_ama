# Classes, Objects and OOPS in Python


## 1. Why we use Classes

**Discussion Question:**
*"What  risks arise when state and behavior are decoupled in a large-scale application?"*

**Concept Overview:** 
In procedural programming, data structures and the functions that modify them are strictly decoupled. As a system scales, this separation can lead to data integrity issues and fragile code architectures.

**Code Implementation:**
```python
# State Representation
pokemon = {"name": "Squirtle", "hp": 44}

# Behavior Implementation
def attack(defender):
    defender["hp"] -= 10

attack(pokemon)

```

---

## 2. Classes and Objects: Blueprints and Instances

**Concept Overview:**
A **Class** serves as a structural blueprint defining the properties and capabilities of an entity. An **Object** (or instance) is the physical realization of that class, occupying distinct memory space.

**Code Implementation:**

```python
class Pokemon:
    pass 

# Instantiation
p1 = Pokemon()
p2 = Pokemon()

print(p1 == p2)

```

**Discussion Question:**
*"Given that two instances are generated from identical class definitions, how does the Python interpreter differentiate them in memory?"*

---

## 3. Initialization and Instance Attributes

**Concept Overview:**
The `__init__` constructor initializes the object's initial state upon creation. **Instance Attributes** are variables tightly bound to a specific object, storing its unique data.

**Code Implementation:**

```python
class Pokemon:
    def __init__(self, name, hp):
        self.name = name  
        self.hp = hp

charmander = Pokemon("Charmander", 39)
print(charmander.name)

```

**Discussion Question:**
*"What is the specific role of the `self` parameter during object instantiation?"*

---

## 4. Methods: Encapsulating Behavior

**Concept Overview:**
Methods are functions defined within a class. They represent the actions or behaviors an object can execute, often manipulating the object's internal state.

**Code Implementation:**

```python
class Pokemon:
    def __init__(self, name, hp):
        self.name = name
        self.hp = hp

    def take_damage(self, damage):
        self.hp -= damage
        print(f"{self.name} took {damage} damage! HP is {self.hp}")

bulbasaur = Pokemon("Bulbasaur", 45)
bulbasaur.take_damage(15) 

```

**Discussion Question:**
*"When invoking an instance method, why is the argument count in the method call one less than the parameter count in the method signature?"*

---

## 5. Inheritance: Hierarchical Code Reusability

**Concept Overview:**
Inheritance allows a child class to derive attributes and methods from a parent class. This facilitates DRY (Don't Repeat Yourself) principles by sharing base logic while permitting specialized extensions.

**Code Implementation:**

```python
# Base Class (Parent)
class Pokemon:
    def __init__(self, name, hp):
        self.name = name
        self.hp = hp

# Derived Class (Child)
class FirePokemon(Pokemon):
    def __init__(self, name, hp, fire_power):
        super().__init__(name, hp)   
        self.fire_power = fire_power 

charizard = FirePokemon("Charizard", 100, 50)

```

**Discussion Question:**
*"If a derived class does not explicitly define a specific method, what mechanism does the interpreter use to resolve the method call?"*

---

## 6. Polymorphism: Interface Consistency

**Concept Overview:**
Polymorphism ensures that disparate classes can be treated uniformly. Different derived classes can implement the exact same method signature but execute unique internal logic.

**Code Implementation:**

```python
class WaterPokemon(Pokemon):
    def attack(self):
        print(f"{self.name} uses Water Gun!")

class ElectricPokemon(Pokemon):
    def attack(self):
        print(f"{self.name} uses Thunderbolt!")

squirtle = WaterPokemon("Squirtle", 44)
pikachu = ElectricPokemon("Pikachu", 35)

squirtle.attack()
pikachu.attack()

```

**Discussion Question:**
*"How does polymorphism reduce conditional complexity in a main application loop?"*

---

## 7. Encapsulation: Data Integrity and Access Modifiers

**Concept Overview:**
Encapsulation restricts direct access to an object's internal state. In Python, prefixing an attribute with double underscores (`__`) applies name mangling, enforcing the use of designated methods to access or mutate data safely.

**Code Implementation:**

```python
class Pokemon:
    def __init__(self, name, hp):
        self.name = name
        self.__hp = hp # Private attribute

    def get_hp(self):
        return self.__hp

mewtwo = Pokemon("Mewtwo", 150)
print(f"Mewtwo's HP: {mewtwo.get_hp()}")

```

---

## 8. The `@property` Decorator: Pythonic Getters and Setters

**Concept Overview:**
The `@property` decorator allows developers to implement strict access control and validation logic while exposing an interface that mimics simple variable assignment.

**Code Implementation:**

```python
class Pokemon:
    def __init__(self, name, hp):
        self.name = name
        self._hp = hp 

    @property 
    def hp(self):
        return self._hp

    @hp.setter 
    def hp(self, new_hp):
        if new_hp > 100:
            print("Max HP is 100!")
            self._hp = 100
        else:
            self._hp = new_hp

pikachu = Pokemon("Pikachu", 50)
pikachu.hp = 999 
print(pikachu.hp) # Output: 100
```

## 9. Class vs. Instance Attributes: Global Environment (Weather Systems)

**Concept Overview:** 
Instance attributes represent the localized state of a single entity. Class Attributes act as a centralized, global state shared across all instances. Modifying a class attribute instantly alters the operational environment for every object without requiring the game engine to loop over every active entity.

**Code Implementation:**
```python
class Pokemon:
    # Class Attribute: The global weather state affecting all instances
    current_weather = "Clear" 

    def __init__(self, name, elemental_type, base_power):
        self.name = name
        self.elemental_type = elemental_type
        self.base_power = base_power # Instance Attribute

    def calculate_attack_power(self):
        multiplier = 1.0
        if Pokemon.current_weather == "Rain":
            if self.elemental_type == "Water":
                multiplier = 1.5
            elif self.elemental_type == "Fire":
                multiplier = 0.5
                
        return self.base_power * multiplier

charizard = Pokemon("Charizard", "Fire", 100)
blastoise = Pokemon("Blastoise", "Water", 100)

print(f"Normal Fire Damage: {charizard.calculate_attack_power()}") 

# The global rule is updated ONCE.
print("It started to rain heavily!")
Pokemon.current_weather = "Rain" 

print(f"Rain Fire Damage: {charizard.calculate_attack_power()}")   
print(f"Rain Water Damage: {blastoise.calculate_attack_power()}")

```

**Discussion Question:**
*"If we had used an instance attribute for the `current_weather` instead of a class attribute, what computational bottleneck would occur?"*

---

## 10. Class Methods (`@classmethod`): 

**Concept Overview:**
Class methods receive the class itself (cls) as an implicit first argument rather than the instance. They are frequently utilized to establish alternative constructors for instantiating objects under different initial conditions.

**Code Implementation:**

```python
class Pokemon:
    def __init__(self, name, level):
        self.name = name
        self.level = level

    @classmethod
    def hatch_from_egg(cls, name):
        print("Initialization via Egg Hatching Sequence...")
        return cls(name, level=1) 

togepi = Pokemon.hatch_from_egg("Togepi")
```

**Discussion Question:**
"What does cls do?"

---

## 11. Magic (Dunder) Methods: Operator Overloading

**Concept Overview:**
Magic methods (double underscore methods) allow custom classes to interface seamlessly with Python's built-in operators and functions, creating a more intuitive API.

**Code Implementation:**

```python
class Pokemon:
    def __init__(self, name, hp):
        self.name = name
        self.hp = hp

    def __str__(self):
        return f"🎮 {self.name} (HP: {self.hp})"

    def __add__(self, other_pokemon):
        new_specie = f"{self.name}-{other_pokemon.name} Hybrid"
        return Pokemon(new_specie, hp=10)

charizard = Pokemon("Charizard", 100)
blastoise = Pokemon("Blastoise", 120)

new_specie = charizard + blastoise 
print(new_specie)
```


