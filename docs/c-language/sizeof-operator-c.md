---
title: sizeof — operator (C)
ms.date: 11/04/2016
f1_keywords:
- sizeof
helpviewer_keywords:
- sizeof operator
ms.assetid: 70826d03-3451-41e4-bebb-a820ae66d53f
ms.openlocfilehash: 1d06fc8b541cbce3771a485c8f71953be8f7d552
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229522"
---
# <a name="sizeof-operator-c"></a>sizeof — operator (C)

**`sizeof`** Operator zwraca ilość miejsca do magazynowania (w bajtach) wymaganą do przechowywania obiektu typu operandu. Ten operator pozwala uniknąć określania rozmiarów danych zależnych od maszyn w programach.

## <a name="syntax"></a>Składnia

```
sizeof unary-expression
sizeof ( type-name )
```

## <a name="remarks"></a>Uwagi

Operand jest identyfikatorem, który jest *wyrażeniem jednoargumentowym*lub wyrażeniem rzutowania typu (oznacza to, że specyfikator typu jest ujęty w nawiasy). *Wyrażenie jednoargumentowe* nie może reprezentować obiektu bitowego, niekompletnego typu ani oznaczenia funkcji. Wynik jest nieoznaczoną stałą całkowitą. Standardowy nagłówek STDDEF. H definiuje ten typ jako **size_t**.

Po zastosowaniu **`sizeof`** operatora do identyfikatora tablicy, wynik jest rozmiarem całej tablicy, a nie rozmiarem wskaźnika reprezentowanego przez identyfikator tablicy.

W przypadku zastosowania **`sizeof`** operatora do nazwy typu struktury lub Unii lub do identyfikatora struktury lub typu Unii wynik jest liczbą bajtów w strukturze lub Unii, łącznie z dopełnieniem wewnętrznym i końcowym. Ten rozmiar może obejmować wypełnienie wewnętrzne i końcowe używane do dostosowywania elementów członkowskich struktury lub unii w granicach pamięci. Jednakże, wynik może nie odpowiadać wielkości obliczonej przez dodanie pamięci wymaganej przez poszczególne elementy członkowskie.

Jeśli tablica o niezmienionym rozmiarze jest ostatnim elementem struktury, **`sizeof`** operator zwraca rozmiar struktury bez tablicy.

```
buffer = calloc(100, sizeof (int) );
```

W tym przykładzie używa **`sizeof`** operatora do przekazywania rozmiaru **`int`** , który różni się między maszynami jako argumentem funkcji czasu wykonywania o nazwie `calloc` . Wartość zwracana przez funkcję jest przechowywana w `buffer`.

```
static char *strings[] = {
      "this is string one",
      "this is string two",
      "this is string three",
   };
const int string_no = ( sizeof strings ) / ( sizeof strings[0] );
```

W tym przykładzie `strings` jest tablicą wskaźników do **`char`** . Liczbą wskaźników jest liczba elementów w tablicy, ale nie jest ona określona. Można łatwo określić liczbę wskaźników przy użyciu **`sizeof`** operatora, aby obliczyć liczbę elementów w tablicy. **`const`** Wartość całkowita `string_no` zostanie zainicjowana na tę liczbę. Ponieważ nie jest to **`const`** wartość, `string_no` nie można jej zmodyfikować.

## <a name="see-also"></a>Zobacz także

[Operatory języka C](c-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
