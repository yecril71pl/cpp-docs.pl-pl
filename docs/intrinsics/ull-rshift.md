---
title: __ull_rshift | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __ull_rshift
dev_langs:
- C++
helpviewer_keywords:
- ull_rshift intrinsic
- __ull_rshift intrinsic
ms.assetid: b7ff5254-3540-4e6e-b57c-a6c4beb7dca2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f0193bad5b9184e3168c618b9bc4e3afc5e27abc
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ullrshift"></a>__ull_rshift
**Microsoft Specific**  
  
 na x64 przesuwa określoną wartość 64-bitowego za pomocą pierwszego parametru po prawej stronie według liczby bitów określonej za pomocą drugiego parametru.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned __int64 __ull_rshift(   
   unsigned __int64 mask,    
   int nBit   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `mask`  
 64-bitową liczbę całkowitą wartość przesunięcia w prawo.  
  
 [in] `nBit`  
 Liczba bitów, które mają zostać przesunięte modulo 32 na x86 i modulo 64 na x64.  
  
## <a name="return-value"></a>Wartość zwracana  
 Maska przesunięte `nBit` usługi bits.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__ull_rshift`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Jeśli drugi parametr jest większa niż 31 na x86 (63 na x64), który numer jest pobierany modulo 32 (64 na x64) w celu ustalenia liczby bitów, które mają zostać przesunięte. `ull` w nazwie wskazuje `unsigned long long (unsigned __int64)`.  
  
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
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__ll_lshift](../intrinsics/ll-lshift.md)   
 [__ll_rshift](../intrinsics/ll-rshift.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)