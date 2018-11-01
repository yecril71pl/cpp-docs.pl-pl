---
title: _rotl8, _rotl16
ms.date: 11/04/2016
f1_keywords:
- _rotl8
- _rotl16
helpviewer_keywords:
- _rotl8 intrinsic
- _rotl16 intrinsic
ms.assetid: 8c519ab6-aef9-4f07-a387-daee8408368f
ms.openlocfilehash: c294569b94589a0f64519725c72075374308e231
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474168"
---
# <a name="rotl8-rotl16"></a>_rotl8, _rotl16

**Microsoft Specific**

Obróć wartości wejściowe w lewo do najbardziej znaczący bit (BITEM) przez określoną liczbę pozycji bitów.

## <a name="syntax"></a>Składnia

```
unsigned char _rotl8( 
   unsigned char value, 
   unsigned char shift 
);
unsigned short _rotl16( 
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
|`_rotl8`|x86, ARM, x64|
|`_rotl16`|x86, ARM, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

W odróżnieniu od operacji przesunięcia w lewo, podczas wykonywania po lewej stronie obrotu najbardziej znaczące bity, które wychodził poza wysokiej klasy są przenoszone do najmniej znaczących pozycje bitów.

## <a name="example"></a>Przykład

```
// rotl.cpp
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_rotl8, _rotl16)

int main()
{
    unsigned char c = 'A', c1, c2;

    for (int i = 0; i < 8; i++)
    {
       printf_s("Rotating 0x%x left by %d bits gives 0x%x\n", c,
               i, _rotl8(c, i));
    }

    unsigned short s = 0x12;
    int nBit = 10;

    printf_s("Rotating unsigned short 0x%x left by %d bits gives 0x%x\n",
            s, nBit, _rotl16(s, nBit));
}
```

```Output
Rotating 0x41 left by 0 bits gives 0x41
Rotating 0x41 left by 1 bits gives 0x82
Rotating 0x41 left by 2 bits gives 0x5
Rotating 0x41 left by 3 bits gives 0xa
Rotating 0x41 left by 4 bits gives 0x14
Rotating 0x41 left by 5 bits gives 0x28
Rotating 0x41 left by 6 bits gives 0x50
Rotating 0x41 left by 7 bits gives 0xa0
Rotating unsigned short 0x12 left by 10 bits gives 0x4800
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[_rotr8, _rotr16](../intrinsics/rotr8-rotr16.md)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)