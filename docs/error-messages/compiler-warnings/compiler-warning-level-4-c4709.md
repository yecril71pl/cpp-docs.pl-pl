---
title: Kompilatora (poziom 4) ostrzeżenie C4709 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4709
dev_langs:
- C++
helpviewer_keywords:
- C4709
ms.assetid: 8abfdd45-8c70-4c27-b0fb-ca0c3f0fccf9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aab1727ab667a4434805f969b32957e654814166
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295321"
---
# <a name="compiler-warning-level-4-c4709"></a>Kompilator C4709 ostrzegawcze (poziom 4)
operator przecinka wewnątrz wyrażenia indeksu tablicy  
  
 W przypadku przecinka w wyrażenia indeksu tablicy, kompilator używa wartości po przecinku ostatniego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4709:  
  
```  
// C4709.cpp  
// compile with: /W4  
#include <stdio.h>  
  
int main()   
{  
    int arr[2][2];  
    arr[0][0] = 10;  
    arr[0][1] = 11;  
  
    // Prints 10, not 11  
    printf_s("\n%d",arr[0][1,0]);   // C4709  
}  
```