---
title: Funkcje rekursywne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C], recursive
- function calls, recursive
- functions [C], calling recursively
- recursive function calls
ms.assetid: 59739040-3081-4006-abbc-9d8423992bce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 187c176aa90997e4841bc22e468fab079f9e8b2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062764"
---
# <a name="recursive-functions"></a>Funkcje rekursywne

Można wywołać dowolną funkcję w programie C rekursywnie; oznacza to może wywołać sam. Liczba wywołań rekurencyjnych jest ograniczona do rozmiaru stosu. Zobacz [/STACK (twórz stos z alokacji)](../build/reference/stack-stack-allocations.md) (/ STACK) — opcja konsolidatora uzyskać informacji na temat konsolidatora opcje tego Ustaw rozmiar stosu. Każdym wywołaniu funkcji nowy magazyn jest przydzielany dla parametrów i **automatycznie** i **zarejestrować** zmienne, tak aby ich wartości w wywołaniach poprzedniej, niedokończone nie są zastępowane. Parametry są bezpośrednio dostępne jedynie z wystąpieniem funkcji, w którym są tworzone. Poprzednie parametry nie są dostępne dla następujących wystąpień funkcji.

Należy pamiętać, że zmienne zadeklarowane za pomocą **statyczne** magazynu nie wymagają nowego magazynu z każde wywołanie cykliczne. Istnieje ich przechowywania przez okres istnienia programu. Każde odwołanie do zmiennej takie uzyskuje dostęp do tego samego obszaru pamięci masowej.

## <a name="example"></a>Przykład

Ten przykład ilustruje rekursywne wywołania:

```C
int factorial( int num );      /* Function prototype */

int main()
{
    int result, number;
    .
    .
    .
    result = factorial( number );
}

int factorial( int num )      /* Function definition */
{
    .
    .
    .
    if ( ( num > 0 ) || ( num <= 10 ) )
        return( num * factorial( num - 1 ) );
}
```

## <a name="see-also"></a>Zobacz też

[Wywołania funkcji](../c-language/function-calls.md)