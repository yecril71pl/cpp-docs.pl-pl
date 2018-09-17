---
title: __umulh | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __umulh
dev_langs:
- C++
helpviewer_keywords:
- __umulh intrinsic
ms.assetid: d241b53a-e6f7-4af1-9f6e-84e149158f03
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07d1bf4dcf942fe358b0367f02ed0486ee10bd39
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706917"
---
# <a name="umulh"></a>__umulh
**Microsoft Specific**  
  
 Zwróć wysokiej 64-bitowy iloczyn dwóch liczb całkowitych bez znaku 64-bitowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned __int64 __umulh(   
   unsigned __int64 a,   
   unsigned __int64 b   
);  
```  
  
#### <a name="parameters"></a>Parametry  
*a*<br/>
[in] Pierwszy numer do pomnożenia.  
  
*b*<br/>
[in] Druga liczba do pomnożenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wysoka 64 bity 128-bitowego wynik mnożenia.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__umulh`|X64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Te procedury są dostępne tylko jako funkcje wewnętrzne.  
  
## <a name="example"></a>Przykład  
  
```  
// umulh.cpp  
// processor: X64  
#include <cstdio>  
#include <intrin.h>  
  
int main()  
{  
    unsigned __int64 i = 0x10;  
    unsigned __int64 j = 0xFEDCBA9876543210;  
    unsigned __int64 k = i * j; // k has the low 64 bits  
                                // of the product.  
    unsigned __int64 result;  
    result = __umulh(i, j); // result has the high 64 bits  
                            // of the product.  
    printf_s("0x%I64x * 0x%I64x = 0x%I64x%I64x \n", i, j, result, k);  
    return 0;  
}  
```  
  
```Output  
0x10 * 0xfedcba9876543210 = 0xfedcba98765432100   
```  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)