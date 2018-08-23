---
title: __ll_rshift | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __ll_rshift_cpp
- __ll_rshift
dev_langs:
- C++
helpviewer_keywords:
- __ll_rshift intrinsic
- ll_rshift intrinsic
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd8189f15f38d5d3008c1f20959573ca9d2337c9
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464846"
---
# <a name="llrshift"></a>__ll_rshift
**Microsoft Specific**  
  
 Przenosi wartość 64-bitową, określonym przez pierwszy parametr w prawo o liczbę bitów określoną w drugim parametrze.  
  
## <a name="syntax"></a>Składnia  
  
```  
__int64 __ll_rshift(  
   __int64 Mask,  
   int nBit  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `Mask`  
 Wartość 64-bitową liczbę całkowitą na przesunięcie w prawo.  
  
 [in] `nBit`  
 Liczba bitów, aby przenieść modulo 64 na x64 i modulo 32 na x86.  
  
## <a name="return-value"></a>Wartość zwracana  
 Maska przesunięte `nBit` usługi bits.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__ll_rshift`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Jeśli drugi parametr jest większa niż 64 na numer jest pobierany modulo 64 (32 na x86), aby określić liczbę bitów, aby przenieść x64 (32 na x86). `ll` Prefiks wskazuje, że jest operacją na `long long`, inną nazwę `__int64`, typ całkowity ze znakiem 64-bitowych.  
  
## <a name="example"></a>Przykład  
  
```  
// ll_rshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ll_rshift)  
  
int main()  
{  
   __int64 Mask = - 0x100;  
   int nBit = 4;  
   cout << hex << Mask << endl;  
   cout << " - " << (- Mask) << endl;  
   Mask = __ll_rshift(Mask, nBit);  
   cout << hex << Mask << endl;  
   cout << " - " << (- Mask) << endl;  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
ffffffffffffff00  
 - 100  
fffffffffffffff0  
 - 10  
```  
  
 **Uwaga** Jeśli `_ull_rshift` było używane, BITEM wartość przesunięte w prawo byłby zero, dzięki czemu oczekiwany wynik może nie zostały uzyskane w przypadku wartości ujemnej.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__ll_lshift](../intrinsics/ll-lshift.md)   
 [__ull_rshift](../intrinsics/ull-rshift.md)