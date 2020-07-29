---
title: Tablice jednowymiarowe
ms.date: 11/04/2016
helpviewer_keywords:
- brackets [ ]
- brackets [ ], arrays
- one-dimensional arrays
- arrays [C++], one-dimensional
- square brackets [ ]
- square brackets [ ], arrays
- subscript expressions
ms.assetid: e28536e5-3b77-46b5-97fd-9b938c771816
ms.openlocfilehash: c310d610b4e4cfc5ae5620d38337a5b8fd5243ef
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226356"
---
# <a name="one-dimensional-arrays"></a>Tablice jednowymiarowe

Wyrażenie przyrostkowe, a po nim wyrażenie w nawiasach kwadratowych (**[]**) jest reprezentacją indeksu elementu obiektu tablicy. Wyrażenie indeksu dolnego reprezentuje wartość w adresie, który jest pozycjami *wyrażenia* poza *wyrażeniem przyrostkowym* , gdy jest wyrażona jako

```
postfix-expression [ expression ]
```

Zazwyczaj wartość reprezentowana przez *wyrażenie przyrostkowe* jest wartością wskaźnika, taką jak identyfikator tablicy, a *wyrażenie* jest wartością całkowitą. Jednakże wszystkie wymagane syntaktycznie to, że jedno z wyrażeń jest typu wskaźnika, a drugi jako typ całkowity. W ten sposób wartość całkowita może znajdować się w pozycji *wyrażenia przyrostkowego* , a wartość wskaźnika może być w nawiasach w *wyrażeniu*lub "indeks dolny". Na przykład ten kod jest dozwolony:

```c
// one_dimensional_arrays.c
int sum, *ptr, a[10];
int main() {
   ptr = a;
   sum = 4[ptr];
}
```

Wyrażenia indeksu dolnego są zwykle używane do odwoływania się do elementów tablicy, ale można zastosować indeks dolny do dowolnego wskaźnika. Niezależnie od kolejności wartości *wyrażenie* musi być ujęte w nawiasy kwadratowe (**[]**).

Wyrażenie indeksu dolnego jest oceniane przez dodanie wartości całkowitej do wartości wskaźnika, a następnie zastosowanie operatora pośredniego ( <strong>\*</strong> ) do wyniku. (Zobacz [Operatory pośrednie i Address-of](../c-language/indirection-and-address-of-operators.md) dla dyskusji operatora operator pośredni). W efekcie dla jednowymiarowej tablicy następujące cztery wyrażenia są równoważne, przy założeniu, że `a` jest wskaźnikiem i `b` jest liczbą całkowitą:

```
a[b]
*(a + b)
*(b + a)
b[a]
```

Zgodnie z regułami konwersji dla operatora dodawania (biorąc pod uwagę [Operatory addytywne](../c-language/c-additive-operators.md)), wartość całkowita jest konwertowana na przesunięcie adresu przez pomnożenie jej przez długość typu, w którym znajduje się wskaźnik.

Załóżmy na przykład, że identyfikator `line` odwołuje się do tablicy **`int`** wartości. Poniższa procedura służy do obliczania wyrażenia indeksu dolnego `line[ i ]` :

1. Wartość całkowita `i` jest mnożona przez liczbę bajtów zdefiniowanych jako długość **`int`** elementu. Przekonwertowana wartość `i` reprezentuje `i` **`int`** pozycje.

1. Ta przekonwertowana wartość jest dodawana do pierwotnej wartości wskaźnika ( `line` ) w celu uzyskania adresu, który jest przesunięty `i` **`int`** `line` .

1. Operator pośredni jest stosowany do nowego adresu. Wynik jest wartością elementu tablicy w tym miejscu (intuicyjnie, `line [ i ]` ).

Wyrażenie indeksu dolnego `line[0]` reprezentuje wartość pierwszego elementu wiersza, ponieważ przesunięcie od adresu reprezentowanego przez `line` wynosi 0. Analogicznie, wyrażenie takie jak `line[5]` odwołuje się do elementu przesunięte pięć pozycji z wiersza lub szóstego elementu tablicy.

## <a name="see-also"></a>Zobacz także

[Operator indeksu dolnego:](../cpp/subscript-operator.md)
