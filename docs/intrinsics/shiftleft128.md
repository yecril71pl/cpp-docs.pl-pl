---
title: __shiftleft128 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __shiftleft128
dev_langs:
- C++
helpviewer_keywords:
- __shiftleft128 intrinsic
ms.assetid: 557b846a-8fb0-469d-91ac-1b1fad80dc2a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1e66a1a4faf71649970181bd9d7b47d3da292f24
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="shiftleft128"></a>__shiftleft128
**Microsoft Specific**  
  
 Przenosi ilość 128-bitowego, reprezentowane jako dwie liczb 64-bitowych `LowPart` i `HighPart`, po lewej stronie według liczby bitów określonej `Shift` i zwraca 64 bitów wyniku.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned __int64 __shiftleft128(   
   unsigned __int64 LowPart,   
   unsigned __int64 HighPart,   
   unsigned char Shift   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `LowPart`  
 Niski 64 bity ilość 128-bitowe, które mają zostać przesunięte.  
  
 [in] `HighPart`  
 Wysoka 64 bity ilość 128-bitowe, które mają zostać przesunięte.  
  
 [in] `Shift`  
 Liczba bitów, które mają zostać przesunięte.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wysoka 64 bity wyniku.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__shiftleft128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 `Shift` Wartość jest zawsze modulo 64 tak, na przykład, jeśli wywołujesz `__shiftleft128(1, 0, 64)`, funkcja zostanie przesunięte niski części `0` bitów w lewo i zwracać wysokiej część `0` i nie `1` , ponieważ w przeciwnym razie można się spodziewać.  
  
## <a name="example"></a>Przykład  
  
```  
// shiftleft128.c  
// processor: IPF, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic (__shiftleft128, __shiftright128)  
  
int main()  
{  
    unsigned __int64 i = 0x1I64;  
    unsigned __int64 j = 0x10I64;  
    unsigned __int64 ResultLowPart;  
    unsigned __int64 ResultHighPart;  
  
    ResultLowPart = i << 1;  
    ResultHighPart = __shiftleft128(i, j, 1);  
  
    // concatenate the low and high parts padded with 0's  
    // to display correct hexadecimal 128 bit values  
    printf_s("0x%02I64x%016I64x << 1 = 0x%02I64x%016I64x\n",  
             j, i, ResultHighPart, ResultLowPart);  
  
    ResultHighPart = j >> 1;  
    ResultLowPart = __shiftright128(i, j, 1);  
  
    printf_s("0x%02I64x%016I64x >> 1 = 0x%02I64x%016I64x\n",  
             j, i, ResultHighPart, ResultLowPart);    
}  
```  
  
```Output  
0x100000000000000001 << 1 = 0x200000000000000002  
0x100000000000000001 >> 1 = 0x080000000000000000  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__shiftright128](../intrinsics/shiftright128.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)