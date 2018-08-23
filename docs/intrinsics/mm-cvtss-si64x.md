---
title: _mm_cvtss_si64x | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_cvtss_si64x
dev_langs:
- C++
helpviewer_keywords:
- cvtss2si intrinsic
- _mm_cvtss_si64x intrinsic
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 947c9bf0892da52b44a99486b3ff0f1d59bc6fee
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42466238"
---
# <a name="mmcvtsssi64x"></a>_mm_cvtss_si64x
**Microsoft Specific**  
  
 Generuje x64 rozszerzonej wersji przekonwertować skalarną pojedynczej dokładności liczba zmiennoprzecinkowa na 64-bitowa liczba całkowita (`cvtss2si`) instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
__int64 _mm_cvtss_si64x(   
   __m128 value   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `value`  
 `__m128` Struktury zawierającej — wartości zmiennoprzecinkowe.  
  
## <a name="return-value"></a>Wartość zwracana  
 64-bitową liczbę całkowitą, wynik konwersji pierwsza wartość zmiennoprzecinkowa do liczby całkowitej.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_mm_cvtss_si64x`|X64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy element wartość struktury jest konwertowana na liczbę całkowitą i zwrócony. Zaokrąglenia bity kontrolne w mxcsr rejestru są używane do określenia zachowania zaokrąglania. Domyślny tryb zaokrąglania to zaokrąglony do najbliższej zaokrąglania parzystą liczbą, jeśli część dziesiętną wynosi 0,5. Ponieważ `__m128` struktury reprezentuje rejestrów XMM to wewnętrzne przyjmuje wartość z rejestru XMM i zapisuje je do pamięci systemowej.  
  
 Ta procedura jest dostępna wyłącznie jako wewnętrzna.  
  
## <a name="example"></a>Przykład  
  
```  
// _mm_cvtss_si64x.cpp  
// processor: x64  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvtss_si64x)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    // _mm_load_ps requires an aligned buffer.  
    __declspec(align(16)) float af[4] =  
                           { 101.25, 200.75, 300.5, 400.5 };  
  
    // Load a with the floating point values.  
    // The values will be copied to the XMM registers.  
    a = _mm_load_ps(af);  
  
    // Extract the first element of a and convert to an integer  
    b = _mm_cvtss_si64x(a);  
  
    printf_s("%I64d\n", b);  
}  
```  
  
```Output  
101  
```  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__m128d](../cpp/m128d.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)