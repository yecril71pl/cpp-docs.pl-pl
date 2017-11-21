---
title: Konwersje standardowe i niejawne pakowania | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: boxing, implicit
ms.assetid: 33f7fc7d-5674-44a2-a859-0e6a04fae519
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 69e95168ce68200d24415302f7c87ce63d3858c8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="standard-conversions-and-implicit-boxing"></a>Konwersje standardowe i niejawne konwersje boxing
Konwersja standardowa zostanie wybrany przez kompilator za pośrednictwem konwersji, która wymaga opakowania.  
  
## <a name="example"></a>Przykład  
  
```  
// clr_implicit_boxing_Std_conversion.cpp  
// compile with: /clr  
int f3(int ^ i) {   // requires boxing  
   return 1;  
}  
  
int f3(char c) {   // no boxing required, standard conversion  
   return 2;  
}  
  
int main() {  
   int i = 5;  
   System::Console::WriteLine(f3(i));  
}  
```  
  
```Output  
2  
```  
  
## <a name="see-also"></a>Zobacz też  
 [OPAKOWYWANIE](../windows/boxing-cpp-component-extensions.md)