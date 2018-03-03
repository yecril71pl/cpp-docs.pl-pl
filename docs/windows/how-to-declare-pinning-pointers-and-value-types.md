---
title: "Porady: deklarowanie unieruchamiania wskaźników i typów wartości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- value types, declaring
- pinning pointers
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e928fc267bb9e5ec13aeb4f07718454742e60ded
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-declare-pinning-pointers-and-value-types"></a>Porady: deklarowanie unieruchamiania wskaźników i typów wartości
Można go niejawnie opakować typ wartości. Następnie można zadeklarować przypiętego wskaźnika do obiektu typu wartości się i użyj **pin_ptr** do typu wartości spakowanej.  
  
## <a name="example"></a>Przykład  
  
### <a name="code"></a>Kod  
  
```  
// pin_ptr_value.cpp  
// compile with: /clr  
value struct V {  
   int i;  
};  
  
int main() {  
   V ^ v = gcnew V;   // imnplicit boxing  
   v->i=8;  
   System::Console::WriteLine(v->i);  
   pin_ptr<V> mv = &*v;  
   mv->i = 7;  
   System::Console::WriteLine(v->i);  
   System::Console::WriteLine(mv->i);  
}  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```  
8  
7  
7  
```  
  
## <a name="see-also"></a>Zobacz też  
 [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)