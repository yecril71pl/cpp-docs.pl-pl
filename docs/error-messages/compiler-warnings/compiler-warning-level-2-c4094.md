---
title: Kompilatora (poziom 2) ostrzeżenie C4094 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4094
dev_langs:
- C++
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9deae6a0e21fcb7dd4f09de07e65445dc9595932
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-2-c4094"></a>Kompilator C4094 ostrzegawcze (poziom 2)
nieoznakowanego 'token' zadeklarowany żadnych symboli  
  
 Kompilator wykryto pustej deklaracji przy użyciu struktury nieoznakowanego, Unią lub klasy. Deklaracja jest ignorowana.  
  
## <a name="example"></a>Przykład  
  
```  
// C4094.cpp  
// compile with: /W2  
struct  
{  
};   // C4094  
  
int main()  
{  
}  
```  
  
 Ten warunek generuje błąd w obszarze Zgodność ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).