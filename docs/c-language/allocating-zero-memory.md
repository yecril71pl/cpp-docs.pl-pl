---
title: Przydzielanie pamięci zerowej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc3b7a92cdc8a05c73f15c7cea917d86a3b6bb46
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085059"
---
# <a name="allocating-zero-memory"></a>Przydzielanie pamięci zerowej

**ANSI 4.10.3** zachowanie `calloc`, `malloc`, lub `realloc` działać, jeśli żądany rozmiar wynosi zero

`calloc`, `malloc`, I `realloc` funkcje są akceptowane wartości zerowe jako argument. Nie rzeczywiste pamięć została przydzielona, ale nieprawidłowy wskaźnik jest zwracany i blok pamięci można zmodyfikować później przy realloc.

## <a name="see-also"></a>Zobacz też

[Funkcje bibliotek](../c-language/library-functions.md)