---
title: Kompilatora (poziom 2) ostrzeżenie C4156 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4156
dev_langs:
- C++
helpviewer_keywords:
- C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 249d90712b4a8b02f10deaa4d87cdbb7a7c17ae3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-2-c4156"></a>Kompilator C4156 ostrzegawcze (poziom 2)
Usunięcie wyrażenia tablicowego bez użycia formularza tablicy "delete"; zastąpiono formularz tablicy  
  
 Formularza nie tablicy **usunąć** nie można usunąć tablicy. Kompilator translacji **usunąć** do formularza tablicy.  
  
 To ostrzeżenie występuje tylko w ramach rozszerzenia Microsoft (/Ze).  
  
## <a name="example"></a>Przykład  
  
```  
// C4156.cpp  
// compile with: /W2  
int main()  
{  
   int (*array)[ 10 ] = new int[ 5 ][ 10 ];  
   delete array; // C4156, changed by compiler to "delete [] array;"  
}  
```