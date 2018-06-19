---
title: Kompilatora (poziom 3) ostrzeżenie C4995 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4995
dev_langs:
- C++
helpviewer_keywords:
- C4995
ms.assetid: c6b61755-4730-4947-ad4d-d1c2bc82585a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c6bf1bbab4ee9a5a08a1376c91c6a7bba160625
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291180"
---
# <a name="compiler-warning-level-3-c4995"></a>Kompilator C4995 ostrzegawcze (poziom 3)
"Funkcja": nazwa została oznaczona jako przestarzała #pragma  
  
 Kompilator napotkano funkcję, która została oznaczona atrybutem pragma [przestarzałe](../../preprocessor/deprecated-c-cpp.md). Przyszła wersja prawdopodobnie nie będzie obsługiwała tej funkcji. Możesz wyłączyć to ostrzeżenie o [ostrzeżenie](../../preprocessor/warning.md) pragma (przykład poniżej).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4995:  
  
```  
// C4995.cpp  
// compile with: /W3  
#include <stdio.h>  
  
// #pragma warning(disable : 4995)  
void func1(void)  
{  
    printf("\nIn func1");  
}  
  
int main()   
{  
    func1();  
    #pragma deprecated(func1)  
    func1();   // C4995  
}  
```