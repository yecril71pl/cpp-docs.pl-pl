---
title: __unaligned | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: __unaligned_cpp
dev_langs: C++
helpviewer_keywords: __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: da662cf9cbe17539381766d37255e63d958fb7b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="unaligned"></a>__unaligned
Gdy zadeklarować wskaźnika z `__unaligned` modyfikator, kompilator przyjęto założenie, że wskaźnik adresów dane, które nie jest wyrównany. W rezultacie aplikacji przeznaczonego komputerze rodziny procesora Itanium (IPF), kompilator generuje kod, który odczyta dane niewyrównany jeden naraz.  
  
## <a name="remarks"></a>Uwagi  
 `__unaligned` Modyfikator jest nieprawidłowa dla [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] i [!INCLUDE[vcpritanium](../cpp/includes/vcpritanium_md.md)] kompilatory, ale wpływa na aplikacje tylko IPF komputera docelowego. Modyfikator opisuje wyrównania zaadresowane danych. przyjęto, że wskaźnik sam być wyrównane.  
  
 [!INCLUDE[vcpritanium](../cpp/includes/vcpritanium_md.md)] Procesora generuje błąd wyrównania, gdy uzyskuje dostęp do niespójnych danych i czasu przetwarzania błędu słabnie wydajności. Użyj `__unaligned` modyfikator spowodować procesora do odczytywania danych jednego bajtu w czasie i uniknąć błędów. Modyfikator nie jest wymagane dla [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] aplikacji ponieważ [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] procesora obsługuje niespójnych danych bez spowodowaniem błędu.  
  
 Aby uzyskać więcej informacji na temat wyrównania zobacz:  
  
-   [Dopasuj](../cpp/align-cpp.md)  
  
-   [Operator __alignof](../cpp/alignof-operator.md)  
  
-   [pakiet](../preprocessor/pack.md)  
  
-   [/ZP (wyrównanie członka struktury)](../build/reference/zp-struct-member-alignment.md)  
  
-   [Przykłady wyrównania struktury](../build/examples-of-structure-alignment.md)  
  
## <a name="example"></a>Przykład  
  
```  
// unaligned_keyword.cpp  
// compile with: /c  
// processor: x64 IPF  
#include <stdio.h>  
int main() {  
   char buf[100];  
  
   int __unaligned *p1 = (int*)(&buf[37]);  
   int *p2 = (int *)p1;  
  
   *p1 = 0;   // ok  
  
   __try {  
      *p2 = 0;  // throws an exception  
   }  
   __except(1) {  
      puts("exception");  
   }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)