---
title: Pętla | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- loop_CPP
- vc-pragma.loop
dev_langs:
- C++
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0850a30c0e0e85cd1d90ba5b2399a295a482a3ce
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444674"
---
# <a name="loop"></a>pętla
Określa, jak kod pętli jest uznawana za automatycznego zrównoleglacza i/lub wyłącza pętlę pod uwagę przy automatycznego wektoryzera.  
  
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
  
### <a name="parameters"></a>Parametry  
*hint_parallel(n)*  
Wskazówki, aby kompilator, że ta pętla powinna być przeprowadzana równolegle w *n* wątków, gdzie *n* jest literałem dodatnią liczbą całkowitą lub zerem. Jeśli *n* wynosi zero, maksymalna liczba wątków jest używany w czasie wykonywania. Jest to wskazówka dla kompilatora nie polecenia i nie ma żadnej gwarancji, że pętla będzie odbywać się równolegle. Jeśli pętla zawiera zależności danych lub problemów strukturalnych — na przykład pętla przechowuje do skalaru, który jest używany poza ciało pętli —, a następnie pętli nie będzie zrównoleglona.  
  
Kompilator ignoruje tej opcji, chyba że [/Qpar](../build/reference/qpar-auto-parallelizer.md) określono przełącznika kompilatora.  
  
*no_vector*  
Domyślnie auto-vectorizer jest włączone i podejmie próbę vectorize wszystkich pętli, które ocenia jako korzystających z niej. Określ tej pragmie, aby wyłączyć automatycznego wektoryzera dla pętli, który po nim następuje.  
  
*ivdep*  
Wskazówki dotyczące kompilatorowi ignorowanie wektor zależności dla tej pętli. Użyj tego w połączeniu z *hint_parallel*.  
  
## <a name="remarks"></a>Uwagi  
 
Do użycia **pętli** pragma, umieść go bezpośrednio przed — nie — definicja pętli. Pragmy w życie dla zakresu pętli, który po nim następuje. Wiele dyrektyw pragma można zastosować do pętli, w dowolnej kolejności, ale musi zawierać każdego z nich w instrukcji oddzielne pragmy.  
  
## <a name="see-also"></a>Zobacz też  
 
[Automatyczna paralelizacja i wektoryzacja](../parallel/auto-parallelization-and-auto-vectorization.md)<br/>
[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)