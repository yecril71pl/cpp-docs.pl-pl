---
title: "Kompilatora (poziom 1) ostrzeżenie C4138 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4138
dev_langs: C++
helpviewer_keywords: C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ae173f0862517d7c8d125cc5cf479b84d6463f46
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4138"></a>Kompilator C4138 ostrzegawcze (poziom 1)
"* /" znaleziono poza komentarzem  
  
 Ogranicznik zamknięcia komentarza nie jest poprzedzony ogranicznik otwarcia komentarza. Kompilator zakłada odstęp między gwiazdka (**\***) i ukośnika (/).  
  
## <a name="example"></a>Przykład  
  
```  
// C4138a.cpp  
// compile with: /W1  
int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning  
int main()  
{  
}  
```  
  
 To ostrzeżenie może być spowodowane próby zagnieździć komentarze.  
  
 To ostrzeżenie można rozwiązać, jeśli komentarz fragmentów kodu zawierające komentarze, umieść kod w **#if / #endif** zablokować, a także ustawić na zero kontrolowanie wyrażenia:  
  
```  
// C4138b.cpp  
// compile with: /W1  
#if 0  
int my_variable;   /* Declaration currently not needed */  
#endif  
int main()  
{  
}  
```