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
ms.openlocfilehash: e60a7935cdddc116848b64461b064c5fd5cdd00a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313535"
---
# <a name="arguments"></a>Argumenty

Argumenty w wywołaniu funkcji mają postać:

> *wyrażenie* **(** *wybór wyrażenia-list*<SUB>opt</SUB> **)** /* wywołanie funkcji */

W wywołaniu funkcji *Lista wyrażeń* jest listą wyrażeń (rozdzielonych przecinkami). Wartości tych końcowych wyrażeń są argumentami przekazywanymi do funkcji. Jeśli funkcja nie przyjmuje żadnych argumentów, *Lista wyrażeń* powinna zawierać słowo kluczowe `void`.

Argument może być dowolną wartością typu podstawowego, struktury, unii lub wskaźnika. Wszystkie argumenty są przekazywane przez wartość. Oznacza to, że do odpowiedniego parametru przypisywana jest kopia argumentu. Funkcja nie zna rzeczywistej lokalizacji pamięci przekazanego argumentu. Funkcja używa tej kopii, nie naruszając zmiennej, z której została pierwotnie utworzona.

Chociaż nie można przekazać tablic lub funkcji jako argumentów, można przekazać wskaźniki do tych elementów. Wskaźniki umożliwiają funkcji uzyskanie dostępu do wartości przez odwołanie. Ponieważ wskaźnik do zmiennej przechowuje adres zmiennej, funkcja może użyć tego adresu do uzyskania dostępu do wartości zmiennej. Argumenty wskaźnika pozwalają funkcji na uzyskanie dostępu do tablic i funkcji, pomimo tego, że tablice i funkcje nie mogą być przekazywane jako argumenty.

Kolejność, w jakiej argumenty będą obliczane, może różnić się w różnych kompilatorach i różnych poziomach optymalizacji. Jednakże argumenty i wszelkie efekty uboczne są w pełni obliczane przed wprowadzeniem funkcji. Zobacz [efekty uboczne](../c-language/side-effects.md) , aby uzyskać informacje dotyczące efektów ubocznych.

Oceniana jest *Lista wyrażeń* w wywołaniu funkcji, a typowe konwersje arytmetyczne są wykonywane na każdym z argumentów wywołania funkcji. Jeżeli dostępny jest prototyp, wynikowy typ argumentu jest porównywany z parametrem odpowiadającego prototypu. Jeśli nie są one zgodne, wykonywana jest konwersja lub generowany jest komunikat diagnostyczny. Parametry poddawane są również zwykłym konwersjom arytmetycznym.

Liczba wyrażeń na *liście wyrażeń* musi być zgodna z liczbą parametrów, chyba że prototyp lub definicja funkcji jawnie określa zmienną liczbę argumentów. W tym przypadku kompilator sprawdza tyle argumentów, ile jest nazw typów na liście parametrów i w razie konieczności dokonuje ich konwersji, jak opisano powyżej. Aby uzyskać więcej informacji [, zobacz wywołania o zmiennej liczbie argumentów](../c-language/calls-with-a-variable-number-of-arguments.md) .

Jeśli lista parametrów prototypu zawiera tylko słowo kluczowe `void`, kompilator oczekuje zero argumentów w wywołaniu funkcji i zero parametrów w definicji. W razie napotkania argumentów zgłaszany jest komunikat diagnostyczny.

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

W tym przykładzie funkcja `swap` jest zadeklarowana w `main` tak, że posiada dwa argumenty reprezentowane odpowiednio przez identyfikatory `num1` i `num2`, z których oba są wskaźnikami do wartości `int`. Parametry `num1` i `num2` w definicji stylu prototypu są również zadeklarowane jako wskaźniki do wartości typu `int`.

W wywołaniu funkcji

```C
swap( &x, &y )
```

Adres `x` jest przechowywany w `num1`, a adres `y` jest przechowywany w `num2`. Teraz dla tej samej lokalizacji istnieją dwie nazwy lub „aliasy”. Odwołania do `*num1` i `*num2` w `swap` są faktycznymi odwołaniami do `x` i `y` w `main`. Przypisania w ramach `swap` w rzeczywistości wymieniają zawartość `x` i `y`. W związku z tym nie jest potrzebna żadna instrukcja `return`.

Kompilator przeprowadza kontrolę typów dla argumentów `swap`, ponieważ prototyp `swap` zawiera typy argumentów dla każdego parametru. Identyfikatory między nawiasami prototypu i definicji mogą być takie same lub różne. Ważne jest, aby typy tych argumentów odpowiadały tym z list parametrów prototypu i definicji.

## <a name="see-also"></a>Zobacz też

[Wywołania funkcji](../c-language/function-calls.md)
