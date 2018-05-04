---
title: MxCsr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4f3c229d-0862-4733-acc7-9ed7a0b870ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9df2225526c20463bdbd618322d031c3245d9493
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="mxcsr"></a>MxCsr
Stan rejestru obejmuje również MxCsr. Konwencja wywoływania dzieli rejestr volatile części i nieulotnej części. Volatile części składa się z flagi stanu 6 MXCSR [0:5], a w pozostałej części rejestru MXCSR [6:15] jest uznawany za nieulotnej.  
  
 Części nieulotnej ustawiono na następujące wartości standardowe przy rozpoczęciu wykonywania programu:  
  
```  
MXCSR[6]         : Denormals are zeros - 0  
MXCSR[7:12]      : Exception masks all 1's (all exceptions masked)  
MXCSR[13:14]   : Rounding  control - 0 (round to nearest)  
MXCSR[15]      : Flush to zero for masked underflow - 0 (off)  
```  
  
 Wywoływany, który modyfikuje nieulotnej polach w MXCSR należy przywrócić je przed powrotem do swojego obiektu wywołującego. Ponadto obiekt wywołujący, który został zmodyfikowany w tych polach należy przywrócić ich standardowe wartości przed wywołaniem wywoływany, chyba że umową wywoływany oczekuje wartości zmodyfikowane.  
  
 Istnieją dwa wyjątki od reguł dotyczących innych niż zmienności flagi kontrolne:  
  
-   W funkcjach, gdzie udokumentowane dana funkcja służy do modyfikowania nieulotnej MxCsr flagi.  
  
-   Gdy jest zgodność poprawna, czy naruszenie niniejszych zasad powoduje programy, które działa/oznacza, że taki sam, jak program, gdy te reguły są nie naruszone, na przykład za pomocą analizy całego programu.  
  
 Nie można wykonać o stanie volatile część MXCSR granicy funkcji, chyba że wyraźnie określonych w dokumentacji funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencja wywoływania](../build/calling-convention.md)