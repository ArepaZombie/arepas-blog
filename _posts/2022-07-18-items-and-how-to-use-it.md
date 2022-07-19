---
layout: post
title: Items and how to use it
categories: python
---

## Inspiration

Es curiosa la forma que tiene el arte para cambiarte la vida. Una simple interacción con algo hermoso te puede hacer sentir tantas cosas. Un simple concepto llevado a otro lado, una imagen, una canción, un juego.

He decidido hacer este post en español para que mis palabras puedan fluir de mejor manera porque quiero hablar de como me conmovieron cinco (5) minutos de juego de NetHack.

Era un juego que ya habia probado hace tiempo, fascinado por la idea de los juegos de rol llevados a la maquina con sistemas complejos y graficas sencillas pero al ver lo complejo que era me fui por versiones mas sencillas de la misma receta.

No he probado el limite que lleva este juego, ni siquiera he tocado la punta del iceberg, pero ahora, con este reto encima, veo la pasión y la complejidad que llevó hacer un juego como ese. Si yo sufrí con el simple concepto de hacer un objeto que suba vida o que aumente la defensa en "x" turnos, la complejidad del codigo de NethHack es increible. Es en realidad una obra de arte.

## IT'S ALIVE!

This is the part where I get serious again, and for that I will write in English. It is a very formal language for non-natives. Writing this blog was difficult because the code for this was written a week ago. So this will be a challenge. Reading code.

First of all, the first challenge was to make a way to create *creatures* from data in other file. This way, it will be easier to insert monsters eventually. For that, I created the function *born*, which calls a tuple containing the data required for the creation of a monster. The data will be read by the function and inserted into the creation of a new creature. Simple, but really useful.

{%highlight python%}
#Funcion para crear un monstruo desde una plantilla
def born(data: tuple):
  return creature(data[0],data[1],data[2],data[3],data[4],data[5])
{%endhighlight%}

It's the same thing I made for the items, but I call it *create_item*. And how will I make items work? Well...

## Do you know what it is an *arepa*?

For the items, I created a class that had three (3) values: a *name*, a *action* and a *price*. The first one is a string, the second a tuple, and the last one is an integer. Then how will this work then?

For the first, I create a module within *player* that calls a module within *item* and uses itself as a variable.The *use* module inside the *item* will read the tuple *action* inside the same item. The *action* has two values inside: a *code* and a *quantity*. For example, if the *code* is *LifeUp* and the quantity is 5, this object will restore 5 HP to the player when used.

For simplification, I'll only make positive items that affect the player.

{%highlight python%}
#This is the module for the use of items
def use(self, player: player):
    if self.action[0] == "LifeUp":
      player.hp =+ self.action[1]
      print(f"Estaba buena. +{self.action[1]} de HP")
    elif self.action[0] == "SpeedUp":
      player.sp =+ self.action[1]
      print(f"Uy, calientito. +{self.action[1]} de velocidad por 3 turnos")
    elif self.action[0] == "DefenseUp":
      player.dp =+ self.action[1]
      print(f"Erga, esta potente. +{self.action[1]} de defensa por 3 turnos")
{%endhighlight%}

I've already created the data for three types of items. But now I have to make a system that counts the turns and to erase the item effect given certain turns.

Besides, now I'll have to add this to the function of *fight*.

This will be hard.
