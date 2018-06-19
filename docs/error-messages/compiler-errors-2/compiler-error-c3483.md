---
title: C3483 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3483
dev_langs:
- C++
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e2605674ff701f70f7be6ea1b4158c9f8f0c6ad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33258740"
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