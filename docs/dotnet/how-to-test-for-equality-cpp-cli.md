---
title: "Porady: testowanie równości (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: equality, testing for
ms.assetid: 9115e298-9f75-452d-bdfb-6eeb0fa0b3c6
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 19b573ca0069031cda6d7c8108d51f8bf4fa83ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-test-for-equality-ccli"></a>Porady: testowanie równości (C++/CLI)
W poniższym przykładzie testu równości, która używa rozszerzeń zarządzanych dla języka C++ jest oparta na uchwytów zapoznaj się.  
  
## <a name="example"></a>Przykład  
  
```  
// mcppv2_equality_test.cpp  
// compile with: /clr /LD  
using namespace System;  
  
bool Test1() {  
   String ^ str1 = "test";  
   String ^ str2 = "test";  
   return (str1 == str2);  
}  
```  
  
 IL dla tego programu pokazuje, że wartość zwracana jest implementowane za pomocą wywołania op_Equality.  
  
```  
IL_0012:  call       bool [mscorlib]System.String::op_Equality(string,  
                                                               string)  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Typy zarządzane (C++/CLI)](../dotnet/managed-types-cpp-cli.md)