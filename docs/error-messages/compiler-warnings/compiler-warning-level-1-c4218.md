---
title: Kompilatora (poziom 1) ostrzeżenie C4218 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4218
dev_langs:
- C++
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88b27af84c390760274bb20665eec4452c8e7072
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279753"
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