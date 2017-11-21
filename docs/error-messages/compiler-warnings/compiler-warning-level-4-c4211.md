---
title: "Kompilatora (poziom 4) ostrzeżenie C4211 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4211
dev_langs: C++
helpviewer_keywords: C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9e985dd1a2742fff675642b1dcd1bdddcd8d7379
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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


