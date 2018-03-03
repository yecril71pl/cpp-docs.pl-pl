---
title: FpCsr | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: dff95d5d-7589-4432-82db-64b459c24352
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 15b7caebc99c4724c0e28b7812da8ef224184385
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fpcsr"></a>FpCsr
Stan rejestru obejmuje również x87 FPU słowa formantu. Konwencja wywoływania nakazują tego Zarejestruj, aby być nieulotnej.  
  
 X87 FPU kontroli word rejestru jest ustawiona na następujące wartości standardowych na początku programu wykonywania:  
  
```  
FPCSR[0:6]: Exception masks all 1's (all exceptions masked)  
FPCSR[7]: Reserved - 0  
FPCSR[8:9]: Precision Control - 10B (double precision)  
FPCSR[10:11]: Rounding  control - 0 (round to nearest)  
FPCSR[12]: Infinity control - 0 (not used)  
```  
  
 Wywoływany, który modyfikuje każdego pola w FPCSR należy przywrócić je przed powrotem do swojego obiektu wywołującego. Ponadto obiekt wywołujący, który został zmodyfikowany w tych polach należy przywrócić ich standardowe wartości przed wywołaniem wywoływany, chyba że umową wywoływany oczekuje wartości zmodyfikowane.  
  
 Istnieją dwa wyjątki od reguł dotyczących innych niż zmienności flagi kontrolne:  
  
1.  W funkcjach, gdzie udokumentowane dana funkcja służy do modyfikowania nieulotnej FpCsr flagi.  
  
2.  Gdy jest zgodność poprawna, czy naruszenie niniejszych zasad powoduje programy, które działa/oznacza, że taki sam, jak program, gdy te reguły są nie naruszone, na przykład za pomocą analizy całego programu.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencja wywoływania](../build/calling-convention.md)