---
title: wartość true (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- true_cpp
dev_langs:
- C++
helpviewer_keywords:
- true keyword [C++]
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a469b47d54cef9084ba686538219d62a2d5ec50
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947776"
---
# <a name="true-c"></a>true (C++)
## <a name="syntax"></a>Składnia  
  
```  
  
bool-identifier = true ;  
bool-expression logical-operator true ;  
```  
  
## <a name="remarks"></a>Uwagi  
 To słowo kluczowe jest jedną z dwóch wartości do zmiennej typu [bool](../cpp/bool-cpp.md) lub wyrażenia warunkowego (wyrażenia warunkowego jest teraz wyrażenie logiczne true). Jeśli `i` typu **bool**, then — instrukcja `i = true;` przypisuje **true** do `i`.  
  
## <a name="example"></a>Przykład  
  
```cpp 
// bool_true.cpp  
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