---
title: OMP_SCHEDULE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_SCHEDULE
dev_langs:
- C++
helpviewer_keywords:
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2295a801-e584-4d2f-826f-7ca4c88846a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd5bf96706b94ffbba8cb1b9aeeee8701b266e5d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115050"
---
# <a name="ompschedule"></a>OMP_SCHEDULE
Modyfikuje zachowanie [harmonogram](../../../parallel/openmp/reference/schedule.md) klauzuli podczas `schedule(runtime)` została określona w `for` lub `parallel for` dyrektywy.  
  
## <a name="syntax"></a>Składnia  
  
```  
set OMP_SCHEDULE[=type[,size]]  
```  
  
## <a name="arguments"></a>Argumenty

*Rozmiar*<br/>
(Opcjonalnie) Określa rozmiar iteracji. `size` Musi być dodatnią liczbą całkowitą. Wartość domyślna to 1, chyba że `type` jest statyczna. Jeśli `type` jest `runtime`.  
  
*Typ*<br/>
Rodzaj planowania:  
  
-   `dynamic`  
  
-   `guided`  
  
-   `runtime`  
  
-   `static`  
  
## <a name="remarks"></a>Uwagi  
 Wartość domyślna w implementacji Visual C++ OpenMP standard to `OMP_SCHEDULE=static,0`.  
  
 Aby uzyskać więcej informacji, zobacz [4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md).  
  
## <a name="example"></a>Przykład  
 Następujące polecenie ustawia **OMP_SCHEDULE** zmienną środowiskową:  
  
```  
set OMP_SCHEDULE="guided,2"  
```  
  
 Następujące polecenie wyświetla bieżące ustawienie **OMP_SCHEDULE** zmienną środowiskową:  
  
```  
set OMP_SCHEDULE  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne środowiskowe](../../../parallel/openmp/reference/openmp-environment-variables.md)