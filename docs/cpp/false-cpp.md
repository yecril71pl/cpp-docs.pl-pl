---
title: FALSE (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: false_cpp
dev_langs: C++
helpviewer_keywords: false keyword [C++]
ms.assetid: cc13aec5-1f02-4d38-8dbf-5473ea2b354f
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 041537932670221e359c8d238f98286b9337be3f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="false-c"></a>false (C++)
Słowo kluczowe jest jedną z dwóch wartości dla zmiennej typu [bool](../cpp/bool-cpp.md) lub wyrażenia warunkowego (wyrażenia warunkowego jest teraz **true** wyrażenia logicznego). Na przykład jeśli `i` jest zmienną typu `bool`, `i = false;` przypisuje instrukcji **false** do `i`.  
  
## <a name="example"></a>Przykład  
  
```  
// bool_false.cpp  
#include <stdio.h>  
  
int main()  
{  
    bool bb = true;  
    printf_s("%d\n", bb);  
    bb = false;  
    printf_s("%d\n", bb);  
}  
```  
  
```Output  
1  
0  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)