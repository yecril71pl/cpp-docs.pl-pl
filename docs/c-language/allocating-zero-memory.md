---
title: Przydzielanie pamięci zerowej
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
ms.openlocfilehash: c7d5f307a38fff938c94cf2e1660cec99262a10a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447310"
---
# <a name="allocating-zero-memory"></a>Przydzielanie pamięci zerowej

**ANSI 4.10.3** zachowanie `calloc`, `malloc`, lub `realloc` działać, jeśli żądany rozmiar wynosi zero

`calloc`, `malloc`, I `realloc` funkcje są akceptowane wartości zerowe jako argument. Nie rzeczywiste pamięć została przydzielona, ale nieprawidłowy wskaźnik jest zwracany i blok pamięci można zmodyfikować później przy realloc.

## <a name="see-also"></a>Zobacz też

[Funkcje bibliotek](../c-language/library-functions.md)