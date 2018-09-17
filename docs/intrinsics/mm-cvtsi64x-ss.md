---
title: _mm_cvtsi64x_ss | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_cvtsi64x_ss
dev_langs:
- C++
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb253ab776565339aeaeade26d6d355b4f6a742b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700005"
---
# <a name="mmcvtsi64xss"></a>_mm_cvtsi64x_ss
**Microsoft Specific**  
  
 Generuje x64 rozszerzona wersja liczby całkowitej przekonwertować 64-bitowych wartości zmiennopozycyjna pojedynczej precyzji skalarnych (`cvtsi2ss`) instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
__m128 _mm_cvtsi64x_ss(   
   __m128 a,   
   __int64 b   
);  
```  
  
#### <a name="parameters"></a>Parametry  
*a*<br/>
[in] `__m128` Struktury zawierającej czterech wartości zmiennoprzecinkowych pojedynczej precyzji.  
  
*b*<br/>
[in] 64-bitową liczbę całkowitą do przekonwertowania na wartość zmiennoprzecinkową.  
  
## <a name="return-value"></a>Wartość zwracana  
 `__m128` Strukturę, której pierwsza wartość zmiennoprzecinkowa jest wynik konwersji. Trzy wartości są kopiowane bez zmian od `a`.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_mm_cvtsi64x_ss`|X64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 `__m128` Struktury reprezentuje rejestru XMM, więc w tym wewnętrzne zezwala na wartość `b` z pamięci systemowej do przeniesienia do XMM zarejestrować.  
  
 Ta procedura jest dostępna wyłącznie jako wewnętrzna.  
  
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
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__m128](../cpp/m128.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)