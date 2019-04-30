---
title: Operatory pośrednie i „Address-of”
ms.date: 02/16/2018
helpviewer_keywords:
- address-of operator (&)
- '* operator'
- operators [C++], address-of
- ampersand operator (&)
- '* operator, indirection operator'
- addresses [C++], indirection
- addresses [C++]
- indirection operator
- '& operator, address-of operator'
- null pointers [C++]
- '* operator, address-of operator'
- operators [C++], indirection
ms.assetid: 10d62b00-12ba-4ea9-a2d5-09ac29ca2232
ms.openlocfilehash: 146f84c90aa56b5abf6ae5212c1729022cb7e4dc
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343895"
---
# <a name="indirection-and-address-of-operators"></a>Operatory pośrednie i „Address-of”

Jednoargumentowy operator pośredni (__&#42;__) uzyskuje dostęp do wartości pośrednio, za pomocą wskaźnika. Argument musi być typem wskaźnika. Wynik operacji jest wartością adresowaną przez operand; czyli wartość pod adresem, na który wskazuje operand. Typ wyniku jest typem adresowanym przez operand.

Wynik operatora pośredniego jest *typu* operand jest typu *wskaźnik do typu*. Jeśli operand wskazuje funkcję, wynik jest oznaczeniem funkcji. Jeśli wskazuje on do obiektu, wynik jest wartością lvalue, opisująca obiekt.

Jeśli wartość wskaźnika jest nieprawidłowa, wynik operatora pośredniego jest niezdefiniowane. Oto niektóre z najbardziej typowych warunków, które unieważniają wartość wskaźnika:

- Wskaźnik jest pustym wskaźnikiem.

- Wskaźnik Określa adres obiektu, po zakończeniu jego okres istnienia (np. obiekt, który jest wyjdą poza zakres lub które jest została wycofana) w momencie odwołania.

- Wskaźnik określa adres, który jest nieodpowiednio wyrównany dla typu wskazywanego obiektu.

- Wskaźnik określa adres nieużywany przez program wykonujący.

Jednoargumentowy operator address-of (**&**) podaje adres jego operandu. Argument musi być albo lvalue, opisująca obiekt, który nie został zadeklarowany __zarejestrować__ i nie jest polem bitowym ani wynik jednoargumentowy __&#42;__ tablica lub operator wyłuskania (__&#91; &#93;__) — operator lub oznaczenia funkcji. Wynik jest typu *wskaźnik do typu* dla operandę typu *typu*.

Jeśli argument jest wynikiem jednoargumentowy __&#42;__ operatora, żaden operator jest obliczane i wynikiem jest tak, jakby zostały pominięte oba. Wynik nie jest l-wartością i nadal mają zastosowanie ograniczenia dotyczące operatorów. Jeśli argument jest wynikiem __&#91; &#93;__ operatora, ani __&__ , ani operatora jednoargumentowego __&#42;__ też dorozumianych przez __&#91; &#93;__ operator jest oceniany. Wynik ma taki sam skutek jak usuwanie __&__ operatora i zmieniając __&#91; &#93;__ operatora __+__ operatora. W przeciwnym razie wynik jest wskaźnikiem do obiektu lub funkcji wyznaczony przez operand.

## <a name="examples"></a>Przykłady

W poniższych przykładach użyto tych deklaracji wspólnego:

```C
int *pa, x;
int a[20];
double d;
```

Ta instrukcja używa operatora address-of (**&**) aby pobrać adres szóstego elementu tablicy `a`. Wynik jest przechowywany w zmiennej wskaźnika `pa`:

```C
pa = &a[5];
```

Operator pośredni (__&#42;__) jest używany w tym przykładzie w celu uzyskania dostępu do `int` wartość pod adresem przechowywanym w `pa`. Wartość jest przypisywana do zmiennej całkowitej `x`:

```C
x = *pa;
```

Ten przykład pokazuje, że wynik zastosowania operatora pośredniego do adresu `x` jest taka sama jak `x`:

```C
assert( x == *&x );
```

W tym przykładzie przedstawiono sposoby równoważne zadeklarowaniem wskaźnika do funkcji:

```C
int roundup( void );     /* Function declaration */

int  *proundup  = roundup;
int  *pround  = &roundup;
assert( pround == proundup );
```

Gdy deklarowana jest funkcja `roundup`, deklarowane i inicjowane są dwa wskaźniki do `roundup`. Pierwszy wskaźnik `proundup` jest inicjowany jedynie za pomocą nazwy funkcji, podczas gdy drugi `pround` używa operatora address-of przy inicjalizacji. Inicjalizacje są równoważne.

## <a name="see-also"></a>Zobacz także

[Operator bezpośredni:&#42;](../cpp/indirection-operator-star.md)<br/>
[Operator Address-of: &](../cpp/address-of-operator-amp.md)
