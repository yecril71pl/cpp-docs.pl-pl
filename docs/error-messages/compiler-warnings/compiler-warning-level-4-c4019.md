---
title: "Kompilatora (poziom 4) ostrzeżenie C4019 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4019
dev_langs: C++
helpviewer_keywords: C4019
ms.assetid: 4ecfe85d-673f-4334-8154-36fe7f0b3444
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 89dceba666042423ebb995644cfe612d35917332
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4019"></a>Kompilator C4019 ostrzegawcze (poziom 4)
Instrukcja pusta w globalnym zakresie  
  
 Instrukcja nie jest poprzedzony średnikiem w zakresie globalnym.  
  
 Może zostać ustalona to ostrzeżenie, jeśli usuniesz dodatkowe średnika.  
  
## <a name="example"></a>Przykład  
  
```  
// C4019.c  
// compile with: /Za /W4  
#define declint( varname ) int varname;  
declint( a );   // C4019, int a;;  
declint( b )   // OK, int b;  
  
int main()  
{  
}  
```