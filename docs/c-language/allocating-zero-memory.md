---
title: Przydzielanie pamięci zerowej
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
ms.openlocfilehash: 40f21c0fa9a2a4068cb2592c49ccefed82176a35
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147467"
---
# <a name="allocating-zero-memory"></a>Przydzielanie pamięci zerowej

**ANSI 4.10.3** zachowanie `calloc`, `malloc`, lub `realloc` działać, jeśli żądany rozmiar wynosi zero

`calloc`, `malloc`, I `realloc` funkcje są akceptowane wartości zerowe jako argument. Nie rzeczywiste pamięć została przydzielona, ale nieprawidłowy wskaźnik jest zwracany i blok pamięci można zmodyfikować później przy realloc.

## <a name="see-also"></a>Zobacz także

[Funkcje bibliotek](../c-language/library-functions.md)
