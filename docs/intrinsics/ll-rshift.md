---
title: __ll_rshift | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __ll_rshift_cpp
- __ll_rshift
dev_langs: C++
helpviewer_keywords:
- __ll_rshift intrinsic
- ll_rshift intrinsic
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c0bb658051a4eab579e2c0d2fbb4d6bd525381b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="llrshift"></a>__ll_rshift
**Dotyczące firmy Microsoft**  
  
 Przenosi określoną wartość 64-bitowego za pomocą pierwszego parametru po prawej stronie według liczby bitów określonej przez parametr drugiego.  
  
## <a name="syntax"></a>Składnia  
  
```  
__int64 __ll_rshift(  
   __int64 Mask,  
   int nBit  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`Mask`  
 64-bitową liczbę całkowitą wartość przesunięcia w prawo.  
  
 [in]`nBit`  
 Liczba bitów, które mają zostać przesunięte modulo 64 na x64 i modulo 32 na x86.  
  
## <a name="return-value"></a>Wartość zwracana  
 Maska przesunięte `nBit` usługi bits.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__ll_rshift`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Jeśli drugi parametr jest większa niż 64 na x64 (32 na x86), który numer jest pobierany modulo 64 (32 na x86) w celu ustalenia liczby bitów, które mają zostać przesunięte. `ll` Prefiksu wskazuje, że operacja jest w `long long`, inną nazwę `__int64`, podpisany typ całkowity 64-bitowych.  
  
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
  
 **Uwaga** Jeśli `_ull_rshift` był używany, BITEM wartość przesunięte prawo byłby zero, więc pożądany wynik może być uzyskany w przypadku wartości ujemnej.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__ll_lshift](../intrinsics/ll-lshift.md)   
 [__ull_rshift](../intrinsics/ull-rshift.md)