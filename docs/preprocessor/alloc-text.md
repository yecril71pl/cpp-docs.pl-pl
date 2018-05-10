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
ms.openlocfilehash: a1e07b630254d7691321443a74973e06ed50ae2d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="alloctext"></a>alloc_text
Nazwy sekcji kodu, gdzie się znajdują się definicje określona funkcja. Pragma musi występować między deklarator funkcji i definicji funkcji dla funkcji o nazwie.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma alloc_text( "  
textsection  
", function1, ... )  
```  
  
## <a name="remarks"></a>Uwagi  
 **Alloc_text** pragma nie obsługuje funkcji Członkowskich C++ i funkcji przeciążenia. Ma zastosowanie tylko do funkcji zadeklarowany z powiązaniem C — to znaczy funkcje deklarowane z **zewnętrzne "C"** Specyfikacja powiązania. Jeśli spróbujesz użyć tej pragmy w funkcji z powiązaniem C++, generowany jest błąd kompilatora.  
  
 Ponieważ funkcja adresowania użycie `__based` nie jest obsługiwana, określając lokalizacje sekcji wymaga użycia **alloc_text** pragma. Nazwa określona przez *textsection* powinna zostać ujęta w znaki cudzysłowu.  
  
 **Alloc_text** pragma musi występować po deklaracji dowolnego z określonych funkcji i przed definicjami tych funkcji.  
  
 Funkcje, do którego odwołuje się **alloc_text** pragma powinien być zdefiniowany w tym samym module jako pragma. Jeśli to nie zostanie zrobione, niezdefiniowanej funkcji później jest kompilowany do sekcji inny tekst błędu mogą lub nie może zostać przechwycony. Mimo że program zazwyczaj będzie działać poprawnie, nie można przydzielić funkcji w sekcjach zamierzone.  
  
 Inne ograniczenia dotyczące **alloc_text** są następujące:  
  
-   Nie można używać wewnątrz funkcji.  
  
-   Należy użyć, po funkcja została zadeklarowana, ale przed funkcja została zdefiniowana.  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)