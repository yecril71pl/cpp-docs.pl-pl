---
title: sizeof Operator (C) operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- sizeof
dev_langs:
- C++
helpviewer_keywords:
- sizeof operator
ms.assetid: 70826d03-3451-41e4-bebb-a820ae66d53f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa3c959e4a839521dddc78d97fbf77db2e1c4b99
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080665"
---
# <a name="sizeof-operator-c"></a>sizeof — operator (C)

Operator `sizeof` podaje ilość pamięci w bajtach, wymaganą do przechowywania obiektu typu operand. Ten operator umożliwia Unikaj określania ilości danych zależnych od maszyny w swoich programach.

## <a name="syntax"></a>Składnia

```
sizeof unary-expression
sizeof ( type-name )
```

## <a name="remarks"></a>Uwagi

Argument jest albo identyfikatorem, który jest *jednoargumentowe wyrażenie*, lub wyrażeniem rzutowania typu (oznacza to, czyli typem specyfikatora w nawiasach). *Jednoargumentowe wyrażenie* nie może reprezentować obiektu pola bitowego, niekompletnego typu lub oznaczenia funkcji. Wynik jest nieoznaczoną stałą całkowitą. Standardowy nagłówek STDDEF. H definiuje ten typ jako **size_t**.

Po zastosowaniu operatora `sizeof` do identyfikatora tablicy, wynik jest rozmiarem całej tablicy, a nie rozmiarem wskaźnika reprezentowanego przez identyfikator tablicy.

Po zastosowaniu operatora `sizeof` do nazwy typu struktury lub unii lub identyfikatora typu struktury lub unii, wynik jest liczbą bajtów w strukturze lub unii, w tym wypełnieniem wewnętrznym i końcowym. Ten rozmiar może obejmować wypełnienie wewnętrzne i końcowe używane do dostosowywania elementów członkowskich struktury lub unii w granicach pamięci. Jednakże, wynik może nie odpowiadać wielkości obliczonej przez dodanie pamięci wymaganej przez poszczególne elementy członkowskie.

Jeśli tablica bez określonego rozmiaru jest ostatnim elementem struktury, operator `sizeof` zwróci rozmiar struktury bez tablicy.

```
buffer = calloc(100, sizeof (int) );
```

W poniższym przykładzie użyto operatora `sizeof` do przekazania rozmiaru `int`, który waha się między maszynami, jako argumentu funkcji czasu wykonywania o nazwie `calloc`. Wartość zwracana przez funkcję jest przechowywana w `buffer`.

```
static char *strings[] = {
      "this is string one",
      "this is string two",
      "this is string three",
   };
const int string_no = ( sizeof strings ) / ( sizeof strings[0] );
```

W tym przykładzie `strings` jest tablicą wskaźników do `char`. Liczbą wskaźników jest liczba elementów w tablicy, ale nie jest ona określona. Łatwo jest określić liczbę wskaźników za pomocą operatora `sizeof`, aby obliczyć liczbę elementów w tablicy. **Const** wartość całkowitą `string_no` jest zainicjowana na ten numer. Ponieważ jest on **const** wartość `string_no` nie może być modyfikowany.

## <a name="see-also"></a>Zobacz też

[Operatory języka C](c-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
