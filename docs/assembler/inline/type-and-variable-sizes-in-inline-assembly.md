---
title: Typ i rozmiary zmiennych w zestawie wbudowanym
ms.date: 08/30/2018
ms.topic: reference
helpviewer_keywords:
- variables, length
- size, getting in inline assembly
- size
- LENGTH operator
- TYPE operator
- SIZE operator
- inline assembly, operators
- variables, type
- variables, size
ms.assetid: b62c2f2b-a7ad-4145-bae4-d890db86d348
ms.openlocfilehash: 3e244aaa8ea849b558b77c3f1569820079f6f76c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191615"
---
# <a name="type-and-variable-sizes-in-inline-assembly"></a>Typ i rozmiary zmiennych w zestawie wbudowanym

**Specyficzne dla firmy Microsoft**

Operatory **Length**, **size**i **Type** mają ograniczone znaczenie w zestawie wbudowanym. Nie można ich używać w ogóle z `DUP` operatorem (ponieważ nie można definiować danych przy użyciu dyrektyw lub operatorów MASM). Można jednak użyć ich do znalezienia rozmiaru zmiennych C lub C++ lub typów:

- Operator **Length** może zwracać liczbę elementów w tablicy. Zwraca wartość 1 dla zmiennych nietablicowych.

- Operator **size** może zwrócić rozmiar zmiennej C lub C++. Zmienna size jest produktem o jego **długości** i **typie**.

- Operator **Type** może zwracać rozmiar typu C lub C++ lub zmiennej. Jeśli zmienna jest tablicą, **Typ** zwraca rozmiar pojedynczego elementu tablicy.

Na przykład, jeśli program ma 8-elementową **`int`** tablicę,

```cpp
int arr[8];
```

Poniższe wyrażenia C i Assembly dają rozmiar `arr` i jego elementy.

|__asm|C|Rozmiar|
|-------------|-------|----------|
|**Długość** arr|`sizeof(arr)/sizeof(arr[0])`|8|
|**Rozmiar** arr|`sizeof(arr)`|32|
|**Typ** arr|`sizeof(arr[0])`|4|

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Korzystanie z języka zestawu w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
