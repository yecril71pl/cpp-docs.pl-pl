---
title: _mm_cvtsi64x_ss | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _mm_cvtsi64x_ss
dev_langs: C++
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a567b33e55092e7e8e0361faa0ce54b2498827a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mmcvtsi64xss"></a>_mm_cvtsi64x_ss
**Dotyczące firmy Microsoft**  
  
 Generuje [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] rozszerzona wersja przekonwertować 64-bitową liczbę całkowitą wartość skalarną pojedynczej precyzji Floating-Point (`cvtsi2ss`) instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
__m128 _mm_cvtsi64x_ss(   
   __m128 a,   
   __int64 b   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`a`  
 `__m128` Struktury zawierającej cztery wartości zmiennoprzecinkowych pojedynczej precyzji.  
  
 [in]`b`  
 64-bitową liczbę całkowitą można przekonwertować na wartość zmiennoprzecinkową.  
  
## <a name="return-value"></a>Wartość zwracana  
 `__m128` Struktury, którego pierwsza wartość zmiennoprzecinkowa jest wynikiem konwersji. Trzy wartości są kopiowane z niezmienionym `a`.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_mm_cvtsi64x_ss`|X64|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 `__m128` Rejestru XMM reprezentuje strukturę, więc tym wewnętrzna pozwala wartość `b` w pamięci systemowej do przeniesienia do XMM zarejestrować.  
  
 Ta procedura jest dostępna tylko wewnętrznie.  
  
## <a name="example"></a>Przykład  
  
```  
// _mm_cvtsi64x_ss.cpp  
// processor: x64  
  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvtsi64x_ss)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    a.m128_f32[0] = 0;  
    a.m128_f32[1] = 0;  
    a.m128_f32[2] = 0;  
    a.m128_f32[3] = 0;  
    a = _mm_cvtsi64x_ss(a, b);  
  
    printf_s( "%lf %lf %lf %lf\n",  
              a.m128_f32[0], a.m128_f32[1],   
              a.m128_f32[2], a.m128_f32[3] );  
}  
```  
  
```Output  
54.000000 0.000000 0.000000 0.000000  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__m128](../cpp/m128.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)