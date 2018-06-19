---
title: Kompilatora (poziom 4) ostrzeżenie C4211 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4211
dev_langs:
- C++
helpviewer_keywords:
- C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8112927940e5e2f17a4e74e2855a035bc7d5e5cc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292350"
---
# <a name="compiler-warning-level-4-c4211"></a>Kompilator C4211 ostrzegawcze (poziom 4)
użyto niestandardowego rozszerzenia: ponownie zdefiniowano extern jako static  
  
 Rozszerzenia Microsoft domyślne (/Ze), można ponownie zdefiniować `extern` identyfikator **statycznych**.  
  
## <a name="example"></a>Przykład  
  
```  
// C4211.c  
// compile with: /W4  
extern int i;  
static int i;   // C4211  
  
int main()  
{  
}  
```  
  
 Takie definicji(-e) klas są nieprawidłowe w obszarze Zgodność ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).  
  
## <a name="see-also"></a>Zobacz też  


