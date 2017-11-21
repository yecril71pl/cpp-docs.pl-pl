---
title: "Kompilatora (poziom 1) ostrzeżenie C4218 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4218
dev_langs: C++
helpviewer_keywords: C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 19552c6e836b3fa3f0111b8ab33bc11d33a5699a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4218"></a>Kompilator C4218 ostrzegawcze (poziom 1)
użyto niestandardowego rozszerzenia: należy określić co najmniej klasę magazynu lub typu  
  
 Rozszerzenia Microsoft domyślne (/Ze) można zadeklarować zmiennej bez określenia klasy typu lub magazynu. Jest to domyślny typ `int`.  
  
## <a name="example"></a>Przykład  
  
```  
// C4218.c  
// compile with: /W4  
i;  // C4218  
  
int main()  
{  
}  
```  
  
 Oświadczenia są nieprawidłowe w obszarze Zgodność ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).