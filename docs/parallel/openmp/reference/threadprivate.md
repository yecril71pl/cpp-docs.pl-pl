---
title: threadprivate | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- threadprivate
dev_langs:
- C++
helpviewer_keywords:
- threadprivate OpenMP directive
ms.assetid: 3515aaed-6f9d-4d59-85eb-342378bea2d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9454b33348fa4e4bc2efaa609001201ea215a8c9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081991"
---
# <a name="threadprivate"></a>threadprivate
Określa, czy zmienna jest prywatnego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma omp threadprivate(var)  
```  
  
### <a name="parameters"></a>Parametry
  
*var*<br/>
Rozdzielana przecinkami lista zmiennych, które mają być prywatnego wątku. `var` musi być globalne lub przestrzeń nazw — zmienną o zakresie lub zmiennej lokalnej statycznej.  
  
## <a name="remarks"></a>Uwagi  
 `threadprivate` Dyrektywy nie obsługuje żadnych klauzule OpenMP.  
  
 Aby uzyskać więcej informacji, zobacz [2.7.1 dyrektywa threadprivate](../../../parallel/openmp/2-7-1-threadprivate-directive.md).  
  
 `threadprivate` Dyrektywy opiera się na [wątku](../../../cpp/thread.md) `__declspec` atrybut; limity **__declspec(thread)** dotyczą `threadprivate`.  
  
 Nie można użyć `threadprivate` w każdej biblioteki DLL, który zostanie załadowany za pośrednictwem [LoadLibrary](https://msdn.microsoft.com/library/windows/desktop/ms684175).  Obejmuje to biblioteki dll, które są ładowane z [/delayload (Opóźnij importowanie ładowania)](../../../build/reference/delayload-delay-load-import.md), która także korzysta **LoadLibrary**.  
  
 Możesz użyć `threadprivate` w bibliotece DLL, który statycznie jest ładowany podczas uruchamiania procesu.  
  
 Ponieważ `threadprivate` opiera się na **__declspec(thread)**, `threadprivate` zmienna istnieje w żadnym z wątków pracę w toku, nie tylko te wątki, które są częścią zespołu wątku zduplikowany przez równoległego regionu.  Jest to szczegół implementacji, w których należy wiedzieć, ponieważ można zauważyć, na przykład konstruktory `threadprivate` typu zdefiniowanego przez użytkownika o nazwie więcej często, a następnie oczekuje.  
  
 A `threadprivate` zmienną typu destructable nie musi mieć jej wywołania destruktora.  Na przykład:  
  
```  
struct MyType   
{  
    ~MyType();  
};  
  
MyType threaded_var;  
#pragma omp threadprivate(threaded_var)  
int main()   
{  
    #pragma omp parallel  
    {}  
}  
```  
  
 Użytkownicy mają nie kontrolę tego kiedy spowoduje przerwanie działania wątków stanowiące równoległego regionu.  Jeśli te wątki istnieje podczas procesu, wątki, nie będziesz otrzymywać powiadomienia o zakończenie procesu i destruktor nie zostaną wywołane dla `threaded_var` dotyczące dowolnego wątku, z wyjątkiem tego, który zamyka (tutaj, wątek główny).  Dlatego kod nie powinien liczyć na właściwe zniszczenie `threadprivate` zmiennych.  
  
## <a name="example"></a>Przykład  
 Przykład użycia `threadprivate`, zobacz [prywatnej](../../../parallel/openmp/reference/private-openmp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy](../../../parallel/openmp/reference/openmp-directives.md)