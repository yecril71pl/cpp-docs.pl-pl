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
ms.openlocfilehash: bd3b495483a460f01fe1951ee4c8b5ac3b447701
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232349"
---
# <a name="one-dimensional-arrays"></a>Tablice jednowymiarowe

Wyrażenie przyrostkowe następują wyrażenia w nawiasach kwadratowych (**[**) jest indeksem reprezentacja elementu tablicy obiektów. Wyrażenie indeksu dolnego reprezentuje wartość pod adresem, który jest *wyrażenie* umieszcza poza *wyrażeniem przyrostkowym* wyrażone jako

```
postfix-expression [ expression ]
```

Zwykle reprezentowany przez wartość *wyrażeniem przyrostkowym* jest wartością wskaźnika, takich jak identyfikator tablicy, a *wyrażenie* jest wartością całkowitą. Jednakże, wszystko co jest wymagane składniowo tego jednego z wyrażeń jest typu wskaźnika i innych być typu całkowitego. Ten sposób może być wartością typu całkowitego *wyrażeniem przyrostkowym* położenie i wartość wskaźnika można w nawiasach w *wyrażenie*, lub pozycji "indeksu dolnego,". Na przykład ten kod jest dozwolony:

```
// one_dimensional_arrays.c
int sum, *ptr, a[10];
int main() {
   ptr = a;
   sum = 4[ptr];
}
```

Wyrażenia indeksu dolnego są zazwyczaj używane do odwoływania się do elementów tablicy, ale można zastosować indeks dolny dowolny wskaźnik. Niezależnie od kolejności wartości *wyrażenie* muszą być ujęte w nawiasy kwadratowe (**[**).

Wyrażenie indeksu dolnego jest oceniany przez dodanie wartość całkowitą wartość wskaźnika, a następnie zastosowanie operatora pośredniego (<strong>\*</strong>) do wyniku. (Zobacz [pośredni i Address-of operatory](../c-language/indirection-and-address-of-operators.md) dyskusję na temat operatora pośredniego.) W efekcie Jednowymiarowa tablica następujących czterech wyrażeń są równoważne przy założeniu, że `a` jest wskaźnikiem typu i `b` jest liczbą całkowitą:

```
a[b]
*(a + b)
*(b + a)
b[a]
```

Zgodnie z regułami konwersji, operator dodawania (podano [operatory addytywne](../c-language/c-additive-operators.md)), wartość całkowitą jest konwertowany na przesunięcie adresu mnożąc długość typ adresowany przez wskaźnik myszy.

Na przykład, załóżmy, że identyfikator `line` odwołuje się do tablicy `int` wartości. Poniższa procedura służy do obliczenia wyrażenia indeksu dolnego `line[ i ]`:

1. Wartość całkowita `i` jest mnożony przez liczbę bajtów zdefiniowane jako długość `int` elementu. Przekonwertowana wartości `i` reprezentuje `i` `int` pozycji.

1. Ta wartość przekonwertowanego jest dodawana do oryginalnej wartości wskaźnika (`line`) umożliwiające uzyskanie adres który jest przesunięty `i` `int` umieszcza z `line`.

1. Operator pośredni jest stosowany do nowego adresu. Wynik jest wartością elementu tablicy, w tym miejscu (intuicyjnie `line [ i ]`).

Wyrażenie indeksu dolnego `line[0]` reprezentuje wartość pierwszego elementu wiersza, ponieważ przesunięcie z adresu reprezentowanego przez `line` wynosi 0. Podobnie, wyrażenie, takie jak `line[5]` odwołuje się do pozycji przesunięcia pięciu elementu z wiersza lub szóstego elementu tablicy.

## <a name="see-also"></a>Zobacz także

[Operator indeksu dolnego:](../cpp/subscript-operator.md)
