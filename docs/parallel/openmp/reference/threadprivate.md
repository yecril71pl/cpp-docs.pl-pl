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
ms.openlocfilehash: e7e7edaa36f929750087e3c81f42204ff20e9f62
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="threadprivate"></a>threadprivate
Określa, czy zmienna jest prywatny do wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma omp threadprivate(var)  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `var`  
 Rozdzielana przecinkami lista zmiennych, które mają być prywatne do wątku. `var` musi być zmiennej globalnej lub przestrzeń nazw — zakresu lub lokalna zmienna statyczna.  
  
## <a name="remarks"></a>Uwagi  
 `threadprivate` Dyrektywy obsługuje nie klauzule OpenMP.  
  
 Aby uzyskać więcej informacji, zobacz [2.7.1 dyrektywa dotycząca prywatnego wątku](../../../parallel/openmp/2-7-1-threadprivate-directive.md).  
  
 `threadprivate` Dyrektywa jest oparta na [wątku](../../../cpp/thread.md) `__declspec` atrybutu; limity **__declspec(thread)** dotyczą `threadprivate`.  
  
 Nie można użyć `threadprivate` w każdej biblioteki DLL, który zostanie załadowany za pośrednictwem [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175).  Dotyczy to również bibliotek DLL załadowanych z [/delayload (Opóźnij importowanie ładowania)](../../../build/reference/delayload-delay-load-import.md), który także używa **LoadLibrary**.  
  
 Można użyć `threadprivate` w bibliotece DLL statycznie ładowanej podczas uruchamiania procesu.  
  
 Ponieważ `threadprivate` opiera się na **__declspec(thread)**, `threadprivate` zmienna istnieje w którymkolwiek wątku pracy w toku, nie tylko wątków, które są częścią zespołu wątku zduplikowany przez równoległego regionu.  Jest to szczegóły implementacji, których należy mieć świadomość, ponieważ mogą pojawić się, na przykład konstruktory `threadprivate` typ zdefiniowany przez użytkownika o nazwie więcej często, a następnie oczekuje.  
  
 A `threadprivate` zmiennej typu destructable nie jest gwarantowana mają jego wywołania destruktora.  Na przykład:  
  
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
  
 Użytkownicy mają kontrolka nie określające, kiedy zakończy wątków stanowiące równoległego regionu.  Jeśli istnieje tych wątków, gdy kończy proces, wątków nie zostanie poinformowany o zakończenie procesu i destruktor nie zostanie wywołana dla `threaded_var` w którymkolwiek wątku z wyjątkiem tego, który zamyka (tutaj, wątek głównej).  Tak kod nie powinien count prawidłowego zniszczenie `threadprivate` zmiennych.  
  
## <a name="example"></a>Przykład  
 Na przykład za pomocą `threadprivate`, zobacz [prywatnej](../../../parallel/openmp/reference/private-openmp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy](../../../parallel/openmp/reference/openmp-directives.md)