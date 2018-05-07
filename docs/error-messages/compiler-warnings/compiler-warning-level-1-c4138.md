---
title: Kompilatora (poziom 1) ostrzeżenie C4138 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4138
dev_langs:
- C++
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0865935c30c4934684c7a12e50ab26f3e8b12c4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4138"></a>Kompilator C4138 ostrzegawcze (poziom 1)
"* /" znaleziono poza komentarzem  
  
 Ogranicznik zamknięcia komentarza nie jest poprzedzony ogranicznik otwarcia komentarza. Kompilator zakłada odstęp między gwiazdka (**\****) i ukośnika (/).  
  
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