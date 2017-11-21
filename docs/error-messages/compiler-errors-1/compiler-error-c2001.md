---
title: "C2001 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2001
dev_langs: C++
helpviewer_keywords: C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: aedba438451089aa2d71e06da7ce189ab97d4190
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2001"></a>C2001 błąd kompilatora
nowy wiersz w stałej  
  
 Stałą typu string nie może być kontynuowane w drugim wierszu, jeśli nie możesz wykonać następujące czynności:  
  
-   Zakończenie pierwszy wiersz kreski ułamkowej odwróconej.  
  
-   Zamknij ten ciąg w pierwszym wierszu podwójny cudzysłów i otwórz ciągu w następnym wierszu innego podwójny cudzysłów.  
  
 Kończenie pierwszy wiersz z \n jest niewystarczająca.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2001:  
  
```  
// C2001.cpp  
// C2001 expected  
#include <stdio.h>  
  
int main()  
{  
    printf_s("Hello,  
             world");  
    printf_s("Hello,\n  
             world");  
}  
```  
  
## <a name="example"></a>Przykład  
 Spacje na początku następnego wiersza po znaku kontynuacji wiersza są uwzględniane w stałej ciągu. Brak w przykładach przedstawionych powyżej Osadzanie znaku nowego wiersza w stałej ciągu. Można osadzić znaku nowego wiersza, jak pokazano poniżej:  
  
```  
// C2001b.cpp  
#include <stdio.h>  
  
int main()  
{  
    printf_s("Hello,\n\  
             world");  
  
    printf_s("Hello,\  
             \nworld");  
  
    printf_s("Hello,\n"  
             "world");  
  
    printf_s("Hello,"  
             "\nworld");  
  
    printf_s("Hello,"  
             " world");  
  
    printf_s("Hello,\  
             world");  
}  
```