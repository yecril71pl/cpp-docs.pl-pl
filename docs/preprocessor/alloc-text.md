---
title: alloc_text
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
ms.openlocfilehash: 399e8956a511f289b480e66db7f03cac0a6c7c20
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031368"
---
# <a name="alloctext"></a>alloc_text
Nazwy sekcji kodu, w którym mają znajdować się definicje określonej funkcji. Pragma musi przypadać między deklaratora funkcji i definicji funkcji o nazwie funkcji.

## <a name="syntax"></a>Składnia

```
#pragma alloc_text( "
textsection
", function1, ... )
```

## <a name="remarks"></a>Uwagi

**Alloc_text** nie obsługuje dyrektywy C++ funkcji składowych lub przeciążonych funkcji. Ma ona zastosowanie tylko do funkcji zadeklarowanych z powiązaniem C — oznacza to, że funkcje zadeklarowane za pomocą **extern "C"** Specyfikacja powiązania. Jeśli spróbujesz użyć tej pragmie dla funkcji z powiązaniem C++, jest generowany błąd kompilatora.

Ze względu na używanie adresowania funkcja `__based` nie jest obsługiwana, określając lokalizacje sekcji wymaga użycia **alloc_text** pragmy. Nazwa określona przez *textsection* powinna zostać ujęta w znaki cudzysłowu.

**Alloc_text** pragma musi pojawić się po deklaracjach dowolnego z określonych funkcji i przed definicjami tych funkcji.

Funkcje, do którego odwołuje się **alloc_text** pragma powinien być zdefiniowany w tym samym modułem pragmy. Jeśli nie jest to wykonywane, funkcja undefined później jest skompilowany w sekcji inny tekst błędu może lub nie może zostać przechwycony. Mimo że program zwykle będzie działać poprawnie, funkcja nie zostaną przydzielone w sekcjach zamierzone.

Inne ograniczenia dotyczące **alloc_text** są następujące:

- Nie można używać wewnątrz funkcji.

- Należy użyć, po funkcja została zadeklarowana, ale przed funkcja została zdefiniowana.

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)