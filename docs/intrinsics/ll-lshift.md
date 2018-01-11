---
title: __ll_lshift | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
dev_langs: C++
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 958ade238317d1577bd93d373b9e8ce4aa1f4234
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="lllshift"></a>__ll_lshift
**Dotyczące firmy Microsoft**  
  
 Przesuwa podana wartość 64-bitowe w lewo przez określoną liczbę bitów.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned __int64 __ll_lshift(  
   unsigned __int64 Mask,  
   int nBit  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`Mask`  
 64-bitową liczbę całkowitą wartość przesunięcia w lewo.  
  
 [in]`nBit`  
 Liczba bitów, które mają zostać przesunięte.  
  
## <a name="return-value"></a>Wartość zwracana  
 Maska przesunięte lewej przez `nBit` usługi bits.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__ll_lshift`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Jeśli kompilacja programu przy użyciu architektury 64-bitowe i `nBit` jest większy niż 63, jest liczba bitów, które mają zostać przesunięte `nBit` modulo 64. Jeśli kompilacja programu przy użyciu architektury 32-bitowe i `nBit` jest większy niż 31, jest liczba bitów, które mają zostać przesunięte `nBit` modulo 32.  
  
 `ll` w nazwie wskazuje, że operacja jest w `long long` (`__int64`).  
  
## <a name="example"></a>Przykład  
  
```  
// ll_lshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ll_lshift)  
  
int main()  
{  
   unsigned __int64 Mask = 0x100;  
   int nBit = 8;  
   Mask = __ll_lshift(Mask, nBit);  
   cout << hex << Mask << endl;  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
10000  
```  
  
 **Uwaga** nie ma wersji bez znaku operacji przesunięcia w lewo. Jest to spowodowane `__ll_lshift` używa już parametr wejściowy bez znaku. W odróżnieniu od przesunięcia w prawo Brak ma zależności logowania dla przesunięcia w lewo, ponieważ bitem w wyniku jest zawsze ustawiony na zero, niezależnie od znak wartości przesunięte.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__ll_rshift](../intrinsics/ll-rshift.md)   
 [__ull_rshift](../intrinsics/ull-rshift.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)