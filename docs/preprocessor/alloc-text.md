---
title: alloc_text | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
dev_langs:
- C++
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c90545bb2806b97ccdd47ae90f8ab41bf1b3422c
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465036"
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

**Alloc_text** pragma nie obsługuje funkcji składowych języka C++ lub przeciążonej funkcji. Ma ona zastosowanie tylko do funkcji zadeklarowanych z powiązaniem C — oznacza to, że funkcje zadeklarowane za pomocą **extern "C"** Specyfikacja powiązania. Jeśli spróbujesz użyć tej pragmie dla funkcji z powiązaniem C++, jest generowany błąd kompilatora.  
  
Ze względu na używanie adresowania funkcja `__based` nie jest obsługiwana, określając lokalizacje sekcji wymaga użycia **alloc_text** pragmy. Nazwa określona przez *textsection* powinna zostać ujęta w znaki cudzysłowu.  
  
**Alloc_text** pragma musi pojawić się po deklaracjach dowolnego z określonych funkcji i przed definicjami tych funkcji.  
  
Funkcje, do którego odwołuje się **alloc_text** pragma powinien być zdefiniowany w tym samym modułem pragmy. Jeśli nie jest to wykonywane, funkcja undefined później jest skompilowany w sekcji inny tekst błędu może lub nie może zostać przechwycony. Mimo że program zwykle będzie działać poprawnie, funkcja nie zostaną przydzielone w sekcjach zamierzone.  
  
Inne ograniczenia dotyczące **alloc_text** są następujące:  
  
- Nie można używać wewnątrz funkcji.  
  
- Należy użyć, po funkcja została zadeklarowana, ale przed funkcja została zdefiniowana.  
  
## <a name="see-also"></a>Zobacz też 

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)