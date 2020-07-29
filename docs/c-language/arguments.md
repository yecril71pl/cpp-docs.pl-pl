---
title: Argumenty
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function parameters
- functions [C], parameters
- function parameters, about function parameters
- function arguments
- function calls, arguments
ms.assetid: 14cf0389-2265-41f0-9a96-f2223eb406ca
ms.openlocfilehash: e1c88034044c74a542384873454f993b6bce3244
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232667"
---
# <a name="arguments"></a>Argumenty

Argumenty w wywołaniu funkcji mają postać:

> *wyrażenie* **(** *wybór wyrażenia-list*<SUB>opt</SUB> **)** /* wywołanie funkcji */

W wywołaniu funkcji *Lista wyrażeń* jest listą wyrażeń (rozdzielonych przecinkami). Wartości tych końcowych wyrażeń są argumentami przekazywanymi do funkcji. Jeśli funkcja nie przyjmuje żadnych argumentów, *Lista wyrażeń* powinna zawierać słowo kluczowe **`void`** .

Argument może być dowolną wartością typu podstawowego, struktury, unii lub wskaźnika. Wszystkie argumenty są przekazywane przez wartość. Oznacza to, że do odpowiedniego parametru przypisywana jest kopia argumentu. Funkcja nie zna rzeczywistej lokalizacji pamięci przekazanego argumentu. Funkcja używa tej kopii, nie naruszając zmiennej, z której została pierwotnie utworzona.

Chociaż nie można przekazać tablic lub funkcji jako argumentów, można przekazać wskaźniki do tych elementów. Wskaźniki umożliwiają funkcji uzyskanie dostępu do wartości przez odwołanie. Ponieważ wskaźnik do zmiennej przechowuje adres zmiennej, funkcja może użyć tego adresu do uzyskania dostępu do wartości zmiennej. Argumenty wskaźnika pozwalają funkcji na uzyskanie dostępu do tablic i funkcji, pomimo tego, że tablice i funkcje nie mogą być przekazywane jako argumenty.

Kolejność, w jakiej argumenty będą obliczane, może różnić się w różnych kompilatorach i różnych poziomach optymalizacji. Jednakże argumenty i wszelkie efekty uboczne są w pełni obliczane przed wprowadzeniem funkcji. Zobacz [efekty uboczne](../c-language/side-effects.md) , aby uzyskać informacje dotyczące efektów ubocznych.

Oceniana jest *Lista wyrażeń* w wywołaniu funkcji, a typowe konwersje arytmetyczne są wykonywane na każdym z argumentów wywołania funkcji. Jeżeli dostępny jest prototyp, wynikowy typ argumentu jest porównywany z parametrem odpowiadającego prototypu. Jeśli nie są one zgodne, wykonywana jest konwersja lub generowany jest komunikat diagnostyczny. Parametry poddawane są również zwykłym konwersjom arytmetycznym.

Liczba wyrażeń na *liście wyrażeń* musi być zgodna z liczbą parametrów, chyba że prototyp lub definicja funkcji jawnie określa zmienną liczbę argumentów. W tym przypadku kompilator sprawdza tyle argumentów, ile jest nazw typów na liście parametrów i w razie konieczności dokonuje ich konwersji, jak opisano powyżej. Aby uzyskać więcej informacji [, zobacz wywołania o zmiennej liczbie argumentów](../c-language/calls-with-a-variable-number-of-arguments.md) .

Jeśli lista parametrów prototypu zawiera tylko słowo kluczowe **`void`** , kompilator oczekuje zero argumentów w wywołaniu funkcji i zero parametrów w definicji. W razie napotkania argumentów zgłaszany jest komunikat diagnostyczny.

## <a name="example"></a>Przykład

W tym przykładzie jako argumentów użyto wskaźników:

```C
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

W tym przykładzie `swap` Funkcja jest zadeklarowana w tak, `main` aby miała dwa argumenty, reprezentowane odpowiednio przez identyfikatory `num1` i `num2` , obu, które są wskaźnikami do **`int`** wartości. Parametry `num1` i `num2` w definicji stylu prototypu są również zadeklarowane jako wskaźniki do **`int`** wartości typu.

W wywołaniu funkcji

```C
swap( &x, &y )
```

Adres `x` jest przechowywany w `num1`, a adres `y` jest przechowywany w `num2`. Teraz dla tej samej lokalizacji istnieją dwie nazwy lub „aliasy”. Odwołania do `*num1` i `*num2` w `swap` są faktycznymi odwołaniami do `x` i `y` w `main`. Przypisania w ramach `swap` w rzeczywistości wymieniają zawartość `x` i `y`. W związku z tym nie **`return`** jest wymagana żadna instrukcja.

Kompilator przeprowadza kontrolę typów dla argumentów `swap`, ponieważ prototyp `swap` zawiera typy argumentów dla każdego parametru. Identyfikatory między nawiasami prototypu i definicji mogą być takie same lub różne. Ważne jest, aby typy tych argumentów odpowiadały tym z list parametrów prototypu i definicji.

## <a name="see-also"></a>Zobacz także

[Wywołania funkcji](../c-language/function-calls.md)
