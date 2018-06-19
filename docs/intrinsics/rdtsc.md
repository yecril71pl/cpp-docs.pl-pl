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
ms.openlocfilehash: 81b47a76b3045465d8c3c5c21a87020ee1e74a69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337083"
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