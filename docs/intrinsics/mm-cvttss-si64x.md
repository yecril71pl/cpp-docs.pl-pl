---
title: _mm_cvttss_si64x | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _mm_cvttss_si64x
dev_langs: C++
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fa5dee3ee67678f561a80042c1dc0aab2403a555
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mmcvttsssi64x"></a>_mm_cvttss_si64x
**Dotyczące firmy Microsoft**  
  
 Emituje x64 rozszerzony wersji Konwertuj numerem Floating-Point pojedynczej precyzji obcięcie do 64-bitową liczbę całkowitą (`cvttss2si`) instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
__int64 _mm_cvttss_si64x(   
   __m128 value   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`value`  
 `__m128` Struktury zawierającej wartości zmiennoprzecinkowych pojedynczej precyzji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wynik konwersji pierwszej wartości zmiennoprzecinkowej na 64-bitową liczbę całkowitą.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_mm_cvttss_si64x`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Wewnętrzne różni się od `_mm_cvtss_si64x` tylko w tym niedokładnymi konwersje są obcinane kierunku zera. Ponieważ `__m128` rejestru XMM reprezentuje strukturę, instrukcji wygenerowany przenosi dane z rejestru XMM do pamięci systemowej.  
  
 Ta procedura jest dostępna tylko wewnętrznie.  
  
## <a name="example"></a>Przykład  
  
```  
// _mm_cvttss_si64x.cpp  
// processor: x64  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvttss_si64x)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    // _mm_load_ps requires an aligned buffer.  
    __declspec(align(16)) float af[4] = { 101.5, 200.75,  
                                          300.5, 400.5 };  
  
    // Load a with the floating point values.  
    // The values will be copied to the XMM registers.  
    a = _mm_load_ps(af);  
  
    // Extract the first element of a and convert to an integer  
    b = _mm_cvttss_si64x(a);  
  
    printf_s("%I64d\n", b);  
}  
```  
  
```Output  
101  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__m128](../cpp/m128.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)