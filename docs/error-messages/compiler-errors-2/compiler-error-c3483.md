---
title: C3483 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- C3483
dev_langs:
- C++
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e2ea5c703e9617bd419a3e390f143c0defd7ca9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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