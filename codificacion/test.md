## Codificación

**1) AAABBB.** Imprime números del 1 al 100

* Si es múltiplo de 3, imprime "AAA"
* Si es múltiplo de 5, imprime "BBB"
* Si es múltiplo de 5, imprime "BBB"
* Si es de ambos — “AAA BBB"
* Sino imprime el número

Ejemplo de salida: 1, 2, AAA, 4, BBB, AAA, 7, 8, AAA, BBB, 11, AAA, 13, 14, AAA BBB, 16, 17, AAA, 19, BBB, AAA, 22, 23, AAA, BBB, 26, AAA, 28, 29, AAA BBB, 31, 32, AAA, 34, BBB, AAA, ...

```python
for i in range(1,100):
    if(i%15==0):
        print("AAA BBB")
    elif(i%3==0):
        print("AAA")
    elif(i%5==0):
        print("BBB")
    else:
        print(i)
```


<br/>

**2) Factorial**. Escribe el factorial de un número

* `factorial(4)` = 4! = 1 * 2 * 3 * 4 = 24

def fact(x):
    if(x==1):
        return x
    else:
        return x * fact(x-1)
    
fact(4)

<br/>

**3) Media**. Calcula la media de una lista

* `avg([4, 36, 45, 50, 75]) = 42`

def list_ave(l):
    return sum(l) / len(l)
    
list_ave([4, 36, 45, 50, 75])

<br/>

**4) Borras duplicados**. Elimina duplicados de una lista La lista no está ordenada y el orden de la lista final debe de ser la misma

* `[1, 2, 3, 2]` ⇒ `[1, 2, 3]`
* `[1, 2, 2, 1, 5, 3, 2, 1, 4]` ⇒ `[1, 3, 2, 5, 4]`

**HAY INCONSISTENCIA ENTRE EL EJEMPLO Y LA DESCRIPCIÓN DEL PROBLEMA**

def delete_dup(l):
    unique_items = list(dict.fromkeys(l))
    return unique_items

delete_dup([1,5,2,5,3,2,5])

<br/>

**5) Contar**. Cuantas veces se repite el elemento de una lista

`[1, 3, 2, 1, 5, 3, 5, 1, 4]` ⇒  
* 1: 3 veces
* 2: 1 vez
* 3: 2 veces
* 4: 1 vez
* 5: 2 veces

def countval(l):
    dictio= {i : 0 for i in l}
    for i in l:
        dictio[i]+=1
    return dict(sorted(dictio.items()))

countval([1, 3, 2, 1, 5, 3, 5, 1, 4])    

<br/>

**6) Suma dos**. Dado un array y un número N retorna true si hay números A y B tal que A + B = N. Sino retorna fallo

* `[1, 2, 3, 4], 5` ⇒ `True`
* `[3, 4, 6], 6` ⇒ `False`

def Sumados(l,n):
    for i in range(0,len(l)):
        for j in range(i+1,len(l)):
            if i+j==n:
                return True
    return False

Sumados([1,2,3,4],5)
Sumados([3,4,6],6)

<br/>


**7) Intersection**. Devuelve la intersección de dos listas

* `[1, 2, 4, 6, 10], [2, 4, 5, 7, 10]` ⇒ `[2, 4, 10]`

def intersection(l,l2):
    resul = [value for value in l if value in l2] 
    return resul

intersection([1, 2, 4, 6, 10], [2, 4, 5, 7, 10])
