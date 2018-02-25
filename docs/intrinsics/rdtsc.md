---
title: __rdtsc | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dcf10bebb17096f29e2c96c9d66c631598d023aa
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="rdtsc"></a>__rdtsc
**Microsoft Specific**  
  
 Generuje `rdtsc` instrukcji, która zwraca znacznik czasu procesora. Sygnatura czasowa procesora rejestruje liczbę cykli zegara od ostatniego resetowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned __int64 __rdtsc();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 64-bitowa liczba całkowita bez znaku reprezentujący liczbę cykli.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__rdtsc`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Ta procedura jest dostępna tylko wewnętrznie.  
  
 Interpretacja wartość TSC w tym pokoleniu sprzętu jest inna niż w starszych wersjach [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]. Zobacz instrukcje sprzętu, aby uzyskać więcej informacji.  
  
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
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)