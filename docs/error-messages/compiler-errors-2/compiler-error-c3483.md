---
title: "C3483 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3483
dev_langs: C++
helpviewer_keywords: C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 145e0162c47b360b9d37cf95b108446f919435de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3483"></a>C3483 błąd kompilatora
"var" jest już częścią listy przechwytów lambdy  
  
 Tę samą zmienną są przekazywane do listy przechwytywania lambda wyrażenia więcej niż jeden raz.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń wszystkie dodatkowe wystąpienia zmienną z listy przechwytywania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3483, ponieważ zmienna `n` pojawia się więcej niż jeden raz na liście przechwytywania wyrażenia lambda:  
  
```  
// C3483.cpp  
  
int main()  
{  
   int m = 6, n = 5;  
   [m,n,n] { return n + m; }(); // C3483  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../cpp/lambda-expressions-in-cpp.md)