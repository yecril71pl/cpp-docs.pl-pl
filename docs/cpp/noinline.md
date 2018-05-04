---
title: noinline | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noinline_cpp
dev_langs:
- C++
helpviewer_keywords:
- noinline __declspec keyword
- __declspec keyword [C++], noinline
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f81ab892fd7f406292925f424bebc7514fd7ea0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="noinline"></a>noinline
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 **__declspec(noinline)** informuje kompilator, aby nigdy nie wbudowanej funkcji określonego elementu członkowskiego (funkcja w klasie).  
  
 Może ono być wyodrębnienie wbudowanej funkcji, jeśli jest mała i nie krytyczne znaczenie dla wydajności kodu. Oznacza to czy funkcja jest mała i nie może zostać wywołana często, takich jak funkcja obsługująca warunek błędu.  
  
 Należy pamiętać, że jeśli funkcja jest oznaczony jako `noinline`, funkcji wywołującej będzie mniejsze i w związku z tym sam kandydatem do kompilatora ze śródwierszowaniem.  
  
```  
class X {  
   __declspec(noinline) int mbrfunc() {  
      return 0;   
   }   // will not inline  
};  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [w tekście, __inline, \__forceinline](inline-functions-cpp.md)

