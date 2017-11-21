---
title: "C2092 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2092
dev_langs: C++
helpviewer_keywords: C2092
ms.assetid: 037e44ae-16c8-489a-a512-dcdf7f7795a6
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 45178f653871aea85071aa5df643ebd579f05419
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2092"></a>C2092 błąd kompilatora
Typ elementu tablicy 'Nazwa tablicy' nie może być funkcją  
  
 Tablice funkcje nie są dozwolone. Użyj tablicy wskaźników do funkcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2092:  
  
```  
// C2092.cpp  
typedef void (F) ();  
typedef F AT[10];   // C2092  
```  
  
## <a name="example"></a>Przykład  
 Możliwe rozwiązanie:  
  
```  
// C2092b.cpp  
// compile with: /c  
typedef void (F) ();  
typedef F * AT[10];  
```