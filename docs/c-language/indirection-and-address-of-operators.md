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
ms.openlocfilehash: e631959e69fbdf026886b7a67a3d4e4cd7266989
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229639"
---
# <a name="indirection-and-address-of-operators"></a>Operatory pośrednie i „Address-of”

Jednoargumentowy operator pośredni (__&#42;__) uzyskuje dostęp do wartości pośrednio za pośrednictwem wskaźnika. Argument operacji musi być typem wskaźnika. Wynik operacji jest wartością adresowaną przez operand; czyli wartość pod adresem, na który wskazuje operand. Typ wyniku jest typem adresowanym przez operand.

Wynik operatora pośredni jest *typu* , jeśli operand jest typu *wskaźnika do typu*. Jeśli operand wskazuje funkcję, wynik jest oznaczeniem funkcji. Jeśli wskazuje na obiekt, wynik jest lvalue, który wyznacza obiekt.

Jeśli wartość wskaźnika jest nieprawidłowa, wynik operatora pośredni jest niezdefiniowany. Poniżej przedstawiono niektóre typowe warunki unieważnienia wartości wskaźnika:

- Wskaźnik jest pustym wskaźnikiem.

- Wskaźnik określa adres obiektu po zakończeniu jego okresu istnienia (na przykład obiekt, który został usunięty z zakresu lub został cofnięty przydziału) w momencie odwołania.

- Wskaźnik określa adres, który jest nieodpowiednio wyrównany dla typu wskazywanego obiektu.

- Wskaźnik określa adres nieużywany przez program wykonujący.

Jednoargumentowy adres operatora ( **&** ) zawiera adres operandu. Operand musi być elementem lvalue, który określa obiekt, który nie __jest zadeklarowany, i__ nie jest polem bitowym ani wynikiem jednoargumentowego operatora __&#42;__ lub operatora dereferencji tablicy (__&#91;&#93;__) lub funkcji. Wynik jest typu *wskaźnika do wpisania* dla operandu *typu Type.*

Jeśli operand jest wynikiem jednoargumentowego operatora __&#42;__ , żaden operator nie zostanie oceniony i wynik jest tak, jakby oba zostały pominięte. Wynik nie jest lvalue, a ograniczenia dotyczące operatorów nadal obowiązują. Jeśli operand jest wynikiem operatora __&#91;&#93;__ , nie __&__ jest oceniany operator ani __&#42;__ jednoargumentowy implikowany przez operatora __&#91;&#93;__ . Wynik ma taki sam skutek jak usunięcie __&__ operatora i zmiana operatora __&#91;&#93;__ na __+__ operator. W przeciwnym razie wynik jest wskaźnikiem do obiektu lub funkcji wyznaczono przez operand.

## <a name="examples"></a>Przykłady

Poniższe przykłady używają tych wspólnych deklaracji:

```C
int *pa, x;
int a[20];
double d;
```

Ta instrukcja używa operatora address-of ( **&** ) w celu uzyskania adresu szóstego elementu tablicy `a` . Wynik jest przechowywany w zmiennej wskaźnik `pa` :

```C
pa = &a[5];
```

Operator pośredni (__&#42;__) jest używany w tym przykładzie w celu uzyskania dostępu do **`int`** wartości pod adresem przechowywanym w `pa` . Wartość jest przypisana do zmiennej całkowitej `x` :

```C
x = *pa;
```

Ten przykład pokazuje, że wynik zastosowania operatora pośredni do adresu `x` jest taki sam jak `x` :

```C
assert( x == *&x );
```

W tym przykładzie przedstawiono równoważne sposoby deklarowania wskaźnika do funkcji:

```C
int roundup( void );     /* Function declaration */

int  *proundup  = roundup;
int  *pround  = &roundup;
assert( pround == proundup );
```

Gdy deklarowana jest funkcja `roundup`, deklarowane i inicjowane są dwa wskaźniki do `roundup`. Pierwszy wskaźnik `proundup` jest inicjowany jedynie za pomocą nazwy funkcji, podczas gdy drugi `pround` używa operatora address-of przy inicjalizacji. Inicjalizacje są równoważne.

## <a name="see-also"></a>Zobacz także

[Operator pośredni: &#42;](../cpp/indirection-operator-star.md)<br/>
[Operator Address-of: &](../cpp/address-of-operator-amp.md)
