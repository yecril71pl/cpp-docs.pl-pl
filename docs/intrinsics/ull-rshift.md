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
ms.openlocfilehash: e5248792d04efca518fc425a144c692cd88cf8d1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333121"
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