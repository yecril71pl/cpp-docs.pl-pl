---
title: _rotr8, _rotr16
ms.date: 09/02/2019
f1_keywords:
- _rotr16
- _rotr8
helpviewer_keywords:
- _rotr8 intrinsic
- _rotr16 intrinsic
ms.assetid: dfbd2c82-82b4-427a-ad52-51609027ebff
ms.openlocfilehash: 66598a4e6cdc26fa60a87cd32abaa34319ebe6cc
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218041"
---
# <a name="_rotr8-_rotr16"></a>_rotr8, _rotr16

**Microsoft Specific**

Obróć wartości wejściowe w prawo do najmniej znaczącego bitu (LSB) o określoną liczbę pozycji bitowych.

## <a name="syntax"></a>Składnia

```C
unsigned char _rotr8(
   unsigned char value,
   unsigned char shift
);
unsigned short _rotr16(
   unsigned short value,
   unsigned char shift
);
```

### <a name="parameters"></a>Parametry

*wartościami*\
podczas Wartość do obrócenia.

*nocn*\
podczas Liczba bitów do obrócenia.

## <a name="return-value"></a>Wartość zwracana

Obrócona wartość.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`_rotr8`|x86, ARM, x64, ARM64|
|`_rotr16`|x86, ARM, x64, ARM64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

W przeciwieństwie do operacji przesunięcia w prawo przy wykonywaniu prawego obrotu, bity o niskiej kolejności, które wykraczają poza dolny koniec, są przenoszone do pozycji bitów o dużej kolejności.

## <a name="example"></a>Przykład

```cpp
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

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[_rotl8, _rotl16](../intrinsics/rotl8-rotl16.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
