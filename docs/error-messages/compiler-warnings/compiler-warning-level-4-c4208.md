---
title: Kompilatora (poziom 4) ostrzeżenie C4208 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4208
dev_langs:
- C++
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b61f8b0a6a0ac61982bee79abb81f083d40a48f1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292366"
---
# <a name="compiler-warning-level-4-c4208"></a>Kompilator C4208 ostrzegawcze (poziom 4)
użyto niestandardowego rozszerzenia: delete [exp] - exp obliczono, ale zignorowano  
  
 Rozszerzenia Microsoft (/Ze), możesz usunąć tablicy przy użyciu wartości w nawiasach kwadratowych z [delete operator](../../cpp/delete-operator-cpp.md). Wartość jest ignorowana.  
  
```  
// C4208.cpp  
// compile with: /W4  
int main()  
{  
   int * MyArray = new int[18];  
   delete [18] MyArray;      // C4208  
   MyArray = new int[18];  
   delete [] MyArray;        // ok  
}  
```  
  
 Wartości te są nieprawidłowe w obszarze Zgodność ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).