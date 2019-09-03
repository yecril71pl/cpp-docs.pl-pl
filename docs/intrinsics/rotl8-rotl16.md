---
title: _rotl8, _rotl16
ms.date: 09/02/2019
f1_keywords:
- _rotl8
- _rotl16
helpviewer_keywords:
- _rotl8 intrinsic
- _rotl16 intrinsic
ms.assetid: 8c519ab6-aef9-4f07-a387-daee8408368f
ms.openlocfilehash: 5dffde2d3f830b6ec4ad43865648c27b1defb593
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218028"
---
# <a name="_rotl8-_rotl16"></a>_rotl8, _rotl16

**Microsoft Specific**

Obróć wartości wejściowe w lewo do najbardziej znaczącego bitu (MSB) o określoną liczbę pozycji bitowych.

## <a name="syntax"></a>Składnia

```C
unsigned char _rotl8(
   unsigned char value,
   unsigned char shift
);
unsigned short _rotl16(
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
|`_rotl8`|x86, ARM, x64, ARM64|
|`_rotl16`|x86, ARM, x64, ARM64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

W przeciwieństwie do operacji przesunięcia w lewo, w przypadku wykonywania lewego obrotu, bity o dużej kolejności, które znajdują się na wysokim końcu, są przenoszone do najmniej znaczących pozycji bitowych.

## <a name="example"></a>Przykład

```cpp
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

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[_rotr8, _rotr16](../intrinsics/rotr8-rotr16.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
