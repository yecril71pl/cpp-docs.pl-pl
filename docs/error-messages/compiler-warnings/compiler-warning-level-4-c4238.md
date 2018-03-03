---
title: "Kompilatora (poziom 4) ostrzeżenie C4238 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4238
dev_langs:
- C++
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8e8e52868d97d31243f92307e9bfd158c818c2f8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4238"></a>Kompilator C4238 ostrzegawcze (poziom 4)
użyto niestandardowego rozszerzenia: wartościowanie prawostronne klasy wykorzystane jako wartościowanie lewostronne  
  
 Zgodność z poprzednimi wersjami programu Visual C++, rozszerzenia Microsoft (**/Ze**) umożliwiają używanie typu klasy, jak r-wartości w kontekście, który jawnie lub niejawnie przyjmuje jego adres. W niektórych przypadkach, takich jak na poniższym przykładzie może to być niebezpieczne.  
  
## <a name="example"></a>Przykład  
  
```  
// C4238.cpp  
// compile with: /W4 /c  
struct C {  
   C() {}  
};  
  
C * pC = &C();   // C4238  
```  
  
 To użycie powoduje błąd w obszarze Zgodność ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).