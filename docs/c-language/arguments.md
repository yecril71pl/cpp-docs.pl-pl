---
title: Argumenty | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- arguments [C++], function
- function parameters
- functions [C], parameters
- function parameters, about function parameters
- function arguments
- function calls, arguments
ms.assetid: 14cf0389-2265-41f0-9a96-f2223eb406ca
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 54819766da9ebd002fa4990ca0b9650626b89015
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="arguments"></a>Argumenty
Argumenty w wywołaniu funkcji mają postać:  
  
```  
  
expression  
(  
expression-list <SUB>opt</SUB> )  /* Function call */  
```  
  
 W wywołaniu funkcji *lista wyrażeń* znajduje się lista wyrażeń (oddzielone przecinkami). Wartości tych końcowych wyrażeń są argumentami przekazywanymi do funkcji. Jeśli funkcja nie przyjmuje żadnych argumentów *lista wyrażeń* powinien zawierać słowa kluczowego `void`.  
  
 Argument może być dowolną wartością typu podstawowego, struktury, unii lub wskaźnika. Wszystkie argumenty są przekazywane przez wartość. Oznacza to, że do odpowiedniego parametru przypisywana jest kopia argumentu. Funkcja nie zna rzeczywistej lokalizacji pamięci przekazanego argumentu. Funkcja używa tej kopii, nie naruszając zmiennej, z której została pierwotnie utworzona.  
  
 Chociaż nie można przekazać tablic lub funkcji jako argumentów, można przekazać wskaźniki do tych elementów. Wskaźniki umożliwiają funkcji uzyskanie dostępu do wartości przez odwołanie. Ponieważ wskaźnik do zmiennej przechowuje adres zmiennej, funkcja może użyć tego adresu do uzyskania dostępu do wartości zmiennej. Argumenty wskaźnika pozwalają funkcji na uzyskanie dostępu do tablic i funkcji, pomimo tego, że tablice i funkcje nie mogą być przekazywane jako argumenty.  
  
 Kolejność, w jakiej argumenty będą obliczane, może różnić się w różnych kompilatorach i różnych poziomach optymalizacji. Jednakże argumenty i wszelkie efekty uboczne są w pełni obliczane przed wprowadzeniem funkcji. Zobacz [efekty uboczne](../c-language/side-effects.md) uzyskać informacji o skutki uboczne.  
  
 *Lista wyrażeń* w funkcji wywołanie jest obliczane i popularne konwersje arytmetyczne są wykonywane na każdy argument w wywołaniu funkcji. Jeżeli dostępny jest prototyp, wynikowy typ argumentu jest porównywany z parametrem odpowiadającego prototypu. Jeśli nie są one zgodne, wykonywana jest konwersja lub generowany jest komunikat diagnostyczny. Parametry poddawane są również zwykłym konwersjom arytmetycznym.  
  
 Liczba wyrażeń w *lista wyrażeń* musi być zgodna z liczbą parametrów, chyba że jawnie określa zmienną liczbę argumentów prototypu lub definicji funkcji. W tym przypadku kompilator sprawdza tyle argumentów, ile jest nazw typów na liście parametrów i w razie konieczności dokonuje ich konwersji, jak opisano powyżej. Zobacz [wywołania ze zmienną liczbą argumentów](../c-language/calls-with-a-variable-number-of-arguments.md) Aby uzyskać więcej informacji.  
  
 Jeśli lista parametrów prototypu zawiera tylko słowo kluczowe `void`, kompilator oczekuje zero argumentów w wywołaniu funkcji i zero parametrów w definicji. W razie napotkania argumentów zgłaszany jest komunikat diagnostyczny.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie jako argumentów użyto wskaźników:  
  
```  
int main()  
{  
    /* Function prototype */  
  
    void swap( int *num1, int *num2 );  
    int x, y;  
    .  
    .  
    .  
    swap( &x, &y );  /* Function call */  
}  
  
/* Function definition */  
  
void swap( int *num1, int *num2 )  
{  
    int t;  
  
    t = *num1;  
    *num1 = *num2;  
    *num2 = t;  
}  
```  
  
 W tym przykładzie funkcja `swap` jest zadeklarowana w `main` tak, że posiada dwa argumenty reprezentowane odpowiednio przez identyfikatory `num1` i `num2`, z których oba są wskaźnikami do wartości `int`. Parametry `num1` i `num2` w definicji stylu prototypu są również zadeklarowane jako wskaźniki do wartości typu `int`.  
  
 W wywołaniu funkcji  
  
```  
swap( &x, &y )  
```  
  
 Adres `x` jest przechowywany w `num1`, a adres `y` jest przechowywany w `num2`. Teraz dla tej samej lokalizacji istnieją dwie nazwy lub „aliasy”. Odwołania do `*num1` i `*num2` w `swap` są faktycznymi odwołaniami do `x` i `y` w `main`. Przypisania w ramach `swap` w rzeczywistości wymieniają zawartość `x` i `y`. W związku z tym nie jest potrzebna żadna instrukcja `return`.  
  
 Kompilator przeprowadza kontrolę typów dla argumentów `swap`, ponieważ prototyp `swap` zawiera typy argumentów dla każdego parametru. Identyfikatory między nawiasami prototypu i definicji mogą być takie same lub różne. Ważne jest, aby typy tych argumentów odpowiadały tym z list parametrów prototypu i definicji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wywołania funkcji](../c-language/function-calls.md)