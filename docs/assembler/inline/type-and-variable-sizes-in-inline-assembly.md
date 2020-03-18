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
ms.openlocfilehash: cdb8bddccbea0ef711cb0be4bbac60f7457c625c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441566"
---
# <a name="type-and-variable-sizes-in-inline-assembly"></a>Typ i rozmiary zmiennych w zestawie wbudowanym

**Specyficzne dla firmy Microsoft**

Operatory **Length**, **size**i **Type** mają ograniczone znaczenie w zestawie wbudowanym. Nie można ich używać w ogóle z operatorem `DUP` (ponieważ nie można definiować danych przy użyciu dyrektyw lub operatorów MASM). Można jednak użyć ich do znalezienia rozmiaru C lub C++ zmiennych lub typów:

- Operator **Length** może zwracać liczbę elementów w tablicy. Zwraca wartość 1 dla zmiennych nietablicowych.

- Operator **size** może zwrócić rozmiar C lub C++ zmiennej. Zmienna size jest produktem o jego **długości** i **typie**.

- Operator **Type** może zwracać rozmiar C lub C++ typu lub zmiennej. Jeśli zmienna jest tablicą, **Typ** zwraca rozmiar pojedynczego elementu tablicy.

Na przykład, jeśli program ma 8-elementową tablicę **int** ,

```cpp
int arr[8];
```

Poniższe wyrażenia C i Assembly dają rozmiar `arr` i jego elementów.

|__asm|C|Rozmiar|
|-------------|-------|----------|
|**Długość** arr|`sizeof`(ARR)/`sizeof`(ARR [0])|8|
|**Rozmiar** arr|`sizeof`(ARR)|32|
|**Typ** arr|`sizeof`(ARR [0])|4|

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>