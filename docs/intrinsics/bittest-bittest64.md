---
title: _bittest, _bittest64 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _bittest64
- _bittest_cpp
- _bittest64_cpp
- _bittest
dev_langs: C++
helpviewer_keywords:
- _bittest intrinsic
- _bittest64 intrinsic
- bt instruction
ms.assetid: 15e62afb-abea-4ee7-a6b1-13efa2034937
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 93567b942306b70a34bd3bd7b2d99675b4ddbd51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="bittest-bittest64"></a>_bittest, _bittest64
**Dotyczące firmy Microsoft**  
  
Generuje `bt` instrukcji, która sprawdza, czy bit w pozycji `b` adresu `a`i zwraca wartość tego bit.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned char _bittest(  
   long const *a,  
   long b  
);  
unsigned char _bittest64(  
   __int64 const *a,  
   __int64 b  
);  
```  
  
### <a name="parameters"></a>Parametry  
[in]`a`  
Wskaźnik do pamięci do sprawdzenia.  
  
[in]`b`  
Pozycja bit do testowania.  
  
### <a name="return-value"></a>Wartość zwracana  
Bit na określonej pozycji.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|nagłówek|  
|---------------|------------------|------------|  
|`_bittest`|x86, ARM,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
|`_bittest64`|ARM,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
  
## <a name="remarks"></a>Uwagi  
Ta procedura jest dostępna tylko wewnętrznie.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// bittest.cpp  
// processor: x86, ARM, x64  
  
#include <stdio.h>  
#include <intrin.h>  
  
long num = 78002;  
  
int main()  
{  
    unsigned char bits[32];  
    long nBit;  
  
    printf_s("Number: %d\n", num);  
  
    for (nBit = 0; nBit < 31; nBit++)  
    {  
        bits[nBit] = _bittest(&num, nBit);  
    }  
  
    printf_s("Binary representation:\n");  
    while (nBit--)  
    {  
        if (bits[nBit])  
            printf_s("1");  
        else  
            printf_s("0");  
    }  
}  
```  
  
```Output  
Number: 78002  
Binary representation:  
0000000000000010011000010110010  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)