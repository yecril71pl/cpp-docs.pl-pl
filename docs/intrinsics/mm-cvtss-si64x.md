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
ms.openlocfilehash: 665c52fc0dd0645e25d3014cc28f9fdfba344e2d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332107"
---
# <a name="mmcvtsssi64x"></a>_mm_cvtss_si64x
**Microsoft Specific**  
  
 Generuje [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] rozszerzona wersja przekonwertować skalarną pojedynczego dokładności liczba zmiennoprzecinkowa na 64-bitową liczbę całkowitą (`cvtss2si`) instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
__int64 _mm_cvtss_si64x(   
   __m128 value   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `value`  
 `__m128` Struktury zawierającej wartości zmiennoprzecinkowych.  
  
## <a name="return-value"></a>Wartość zwracana  
 64-bitową liczbę całkowitą, wynik konwersji pierwszej wartości zmiennoprzecinkowej na liczbę całkowitą.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_mm_cvtss_si64x`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy element wartość struktury jest konwertowana na liczbę całkowitą i zwrócony. Zaokrąglania bity kontroli w MXCSR są używane do określania zachowania zaokrąglania. Zaokrąglij do najbliższej zaokrąglania parzystą liczbą w przypadku liczby dziesiętnej 0,5 to domyślny tryb zaokrąglania. Ponieważ `__m128` struktury reprezentuje rejestru XMM, to wewnętrzne przyjmuje wartość z rejestru XMM i zapisuje go w pamięci systemu.  
  
 Ta procedura jest dostępna tylko wewnętrznie.  
  
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
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__m128d](../cpp/m128d.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)