---
title: __rdtsc | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __rdtsc
dev_langs:
- C++
helpviewer_keywords:
- __rdtsc intrinsic
- rdtsc instruction
- Read Time Stamp Counter instruction
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7888f00b1b95a18e839ab61fc8ff28a2646f9875
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42466137"
---
# <a name="rdtsc"></a>__rdtsc
**Microsoft Specific**  
  
 Generuje `rdtsc` instrukcji, która zwraca znacznik czasu procesora. Sygnatura czasowa procesora zlicza liczbę cykli zegara od ostatniego resetu.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned __int64 __rdtsc();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 64-bitowej nieoznaczonej liczby całkowitej reprezentujący liczbę cykli.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__rdtsc`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Ta procedura jest dostępna tylko jako wewnętrzna.  
  
 Interpretacja wartości TSC w tej generacji sprzętowy różni się od we wcześniejszych wersjach programu x64. Zobacz instrukcje sprzętu, aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
  
```  
// rdtsc.cpp  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__rdtsc)  
  
int main()  
{  
    unsigned __int64 i;  
    i = __rdtsc();  
    printf_s("%I64d ticks\n", i);  
}  
```  
  
```Output  
3363423610155519 ticks  
```  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)