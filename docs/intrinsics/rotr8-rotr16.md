---
title: _rotr8, _rotr16 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _rotr16
- _rotr8
dev_langs:
- C++
helpviewer_keywords:
- _rotr8 intrinsic
- _rotr16 intrinsic
ms.assetid: dfbd2c82-82b4-427a-ad52-51609027ebff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 936113d2b59bf089179c6f0c016c8a91c5edc74d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715822"
---
# <a name="rotr8-rotr16"></a>_rotr8, _rotr16
**Microsoft Specific**  
  
 Obróć wartości wejściowe w prawo do najmniej znaczący bit (najmniej znaczący BAJT) przez określoną liczbę pozycji bitów.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned char _rotr8(   
   unsigned char value,   
   unsigned char shift   
);  
unsigned short _rotr16(   
   unsigned short value,   
   unsigned char shift   
);  
```  
  
#### <a name="parameters"></a>Parametry  
*value*<br/>
[in] Wartość, aby obrócić.  
  
*shift*<br/>
[in] Liczba bitów, aby obrócić.  
  
## <a name="return-value"></a>Wartość zwracana  
 Obrócony wartość.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_rotr8`|x86, ARM, x64|  
|`_rotr16`|x86, ARM, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 W odróżnieniu od operacji przesunięcia w prawo, podczas wykonywania prawo obrotu niski znaczące bity, które wychodził poza niskiej klasy są przenoszone do pozycji bitów najwyższego rzędu.  
  
## <a name="example"></a>Przykład  
  
```  
// rotr.cpp  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_rotr8, _rotr16)  
  
int main()  
{  
    unsigned char c = 'A', c1, c2;  
  
    for (int i = 0; i < 8; i++)  
    {  
       printf_s("Rotating 0x%x right by %d bits gives 0x%x\n", c,  
                i, _rotr8(c, i));  
    }  
  
    unsigned short s = 0x12;  
    int nBit = 10;  
  
    printf_s("Rotating unsigned short 0x%x right by %d bits "  
             "gives 0x%x\n",  
            s, nBit, _rotr16(s, nBit));  
}  
```  
  
```Output  
Rotating 0x41 right by 0 bits gives 0x41  
Rotating 0x41 right by 1 bits gives 0xa0  
Rotating 0x41 right by 2 bits gives 0x50  
Rotating 0x41 right by 3 bits gives 0x28  
Rotating 0x41 right by 4 bits gives 0x14  
Rotating 0x41 right by 5 bits gives 0xa  
Rotating 0x41 right by 6 bits gives 0x5  
Rotating 0x41 right by 7 bits gives 0x82  
Rotating unsigned short 0x12 right by 10 bits gives 0x480  
```  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_rotl8, _rotl16](../intrinsics/rotl8-rotl16.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)