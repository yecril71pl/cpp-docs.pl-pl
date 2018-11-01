---
title: Typ i rozmiary zmiennych w zestawie wbudowanym
ms.date: 08/30/2018
ms.topic: reference
f1_keywords:
- length
- Type
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
ms.openlocfilehash: 36c97ee866ca449e9bbcf514e464a13f24f12cd9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539103"
---
# <a name="type-and-variable-sizes-in-inline-assembly"></a>Typ i rozmiary zmiennych w zestawie wbudowanym

**Microsoft Specific**

**Długość**, **rozmiar**, i **typu** operatory mają ograniczone znaczenie w zestawie wbudowanym. Nie można ich używać w każdym z `DUP` — operator (ponieważ nie można zdefiniować danych za pomocą dyrektywy MASM lub operatory). Ale można je znaleźć rozmiar C lub C++ zmiennych lub typów:

- **Długość** operator może zwracać liczbę elementów w tablicy. Zwraca wartość 1 dla zmiennych niebędącego tablicą.

- **Rozmiar** operator może zwrócić rozmiar zmiennej C lub C++. Rozmiar zmiennej jest wynikiem jego **długość** i **typu**.

- **Typu** operator może zwrócić rozmiar typu C lub C++ lub zmiennej. Jeśli zmienna jest tablicą, **typu** zwraca rozmiar pojedynczego elementu tablicy.

Na przykład, jeśli program nie ma elementu 8 **int** tablicy

```cpp
int arr[8];
```

następujących wyrażeń C i zestawu uzyskanie rozmiar `arr` i jej elementów.

|__asm|C|Rozmiar|
|-------------|-------|----------|
|**DŁUGOŚĆ** arr|`sizeof`(arr) /`sizeof`(arr[0])|8|
|**ROZMIAR** arr|`sizeof`(arr)|32|
|**Typ** arr|`sizeof`(arr[0])|4|

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>