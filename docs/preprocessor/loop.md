---
title: "Pętla | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- loop_CPP
- vc-pragma.loop
dev_langs: C++
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2f8e7274ad5da4f0bb3978b18be62952006f8ffd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="loop"></a>pętla
Określa, jak kod pętli jest uważany za zrównoleglenia automatycznego i/lub wyklucza pętlę pod uwagę przez wektoryzowania automatycznego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma loop( hint_parallel(n) )  
```  
  
```  
  
#pragma loop( no_vector )  
```  
  
```  
  
#pragma loop( ivdep )  
```  
  
#### <a name="parameters"></a>Parametry  
 `hint_parallel(` `n` `)`  
 Wskazówki dla kompilatora, które pętla powinna być zarządzana z przetwarzaniem między `n` wątków, gdzie `n` jest literałem dodatnią liczbą całkowitą lub zerem. Jeśli `n` wynosi zero, maksymalna liczba wątków jest używany w czasie wykonywania. Jest to wskazówkę kompilator nie polecenia i nie ma żadnej gwarancji, że będzie zarządzana przetwarzaniem pętli. Jeśli pętli ma zależności danych strukturalnych problemów lub — na przykład przechowuje pętli do używanego poza pętli skalarnej —, a następnie pętla zostanie nie być została zrównoleglona.  
  
 Kompilator ignoruje tej opcji, chyba że [/Qpar](../build/reference/qpar-auto-parallelizer.md) został określony przełącznik kompilatora.  
  
 `no_vector`  
 Domyślnie wektoryzowania automatycznego znajduje się na i podejmie próbę vectorize wszystkie pętli, które ocenia go jako korzystających z niej. Określ tej pragmy wektoryzowania automatycznego pętli występujący go wyłączyć.  
  
 `ivdep`  
 Wskazówki kompilator, aby zignorować wektor zależności dla tego pętli. Użyj tej w połączeniu z `hint_parallel`.  
  
## <a name="remarks"></a>Uwagi  
 Aby użyć `loop` pragma, umieść go bezpośrednio przed — nie znajduje się w — definicja pętli. Pragma wejścia w życie dla zakresu pętli występujący go. Pragma wiele można stosować do pętli, w dowolnej kolejności, ale musi określać każdej z nich w oddzielnych pragma instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Automatyczna Paralelizacja i Wektoryzacja](../parallel/auto-parallelization-and-auto-vectorization.md)   
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)