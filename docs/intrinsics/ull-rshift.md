---
title: __ull_rshift | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __ull_rshift
dev_langs:
- C++
helpviewer_keywords:
- ull_rshift intrinsic
- __ull_rshift intrinsic
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ad07e225afbfe0c69b5115cfb566ef722eb81e3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722666"
---
# <a name="ullrshift"></a>__ull_rshift
**Microsoft Specific**  
  
 na x64 przesuwa wartość 64-bitową, określonym przez pierwszy parametr w prawo o liczbę bitów określoną w drugim parametrze.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned __int64 __ull_rshift(   
   unsigned __int64 mask,    
   int nBit   
);  
```  
  
#### <a name="parameters"></a>Parametry  
*Maska*<br/>
[in] Wartość 64-bitową liczbę całkowitą na przesunięcie w prawo.  
  
*nBit*<br/>
[in] Liczba bitów, aby przenieść modulo 32 na x86 i modulo 64 na x64.  
  
## <a name="return-value"></a>Wartość zwracana  
 Maska przesunięte `nBit` usługi bits.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__ull_rshift`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Jeśli drugi parametr jest większa niż 31 na numer jest pobierany modulo 32 (64 na x64), aby określić liczbę bitów, aby przenieść x86 (63 na x64). `ull` w nazwie wskazuje `unsigned long long (unsigned __int64)`.  
  
## <a name="example"></a>Przykład  
  
```  
// ull_rshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ull_rshift)  
  
int main()  
{  
   unsigned __int64 mask = 0x100;  
   int nBit = 8;  
   mask = __ull_rshift(mask, nBit);  
   cout << hex << mask << endl;  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
1  
```  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__ll_lshift](../intrinsics/ll-lshift.md)   
 [__ll_rshift](../intrinsics/ll-rshift.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)