---
title: __shiftleft128
ms.date: 11/04/2016
f1_keywords:
- __shiftleft128
helpviewer_keywords:
- __shiftleft128 intrinsic
ms.assetid: 557b846a-8fb0-469d-91ac-1b1fad80dc2a
ms.openlocfilehash: 4fb1f9e65210ca9f9e38afd6fc13e01c7eb8f045
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51325571"
---
# <a name="shiftleft128"></a>__shiftleft128

**Microsoft Specific**

Przenosi ilość 128-bitowego, reprezentowane jako dwie ilości 64-bitowych `LowPart` i `HighPart`, w lewo o liczbę bitów określoną przez `Shift` i zwraca wysokiej 64 bity wyniku.

## <a name="syntax"></a>Składnia

```
unsigned __int64 __shiftleft128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

#### <a name="parameters"></a>Parametry

*LowPart*<br/>
[in] Niski 64 bity ilość 128-bitowe przesunięcie.

*HighPart*<br/>
[in] Wysoka 64 bity ilość 128-bitowe przesunięcie.

*SHIFT*<br/>
[in] Liczba bitów, aby przesunąć.

## <a name="return-value"></a>Wartość zwracana

Wysoka 64 bity wyniku.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__shiftleft128`|X64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

`Shift` Wartość jest zawsze modulo 64 więc, na przykład, jeśli wywołasz `__shiftleft128(1, 0, 64)`, funkcja zostanie wprowadzony niskiej część `0` bitów lewej i zwracać wysokiej część `0` i nie `1` w przeciwnym razie może być oczekiwany.

## <a name="example"></a>Przykład

```
// shiftleft128.c
// processor: IPF, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic (__shiftleft128, __shiftright128)

int main()
{
    unsigned __int64 i = 0x1I64;
    unsigned __int64 j = 0x10I64;
    unsigned __int64 ResultLowPart;
    unsigned __int64 ResultHighPart;

    ResultLowPart = i << 1;
    ResultHighPart = __shiftleft128(i, j, 1);

    // concatenate the low and high parts padded with 0's
    // to display correct hexadecimal 128 bit values
    printf_s("0x%02I64x%016I64x << 1 = 0x%02I64x%016I64x\n",
             j, i, ResultHighPart, ResultLowPart);

    ResultHighPart = j >> 1;
    ResultLowPart = __shiftright128(i, j, 1);

    printf_s("0x%02I64x%016I64x >> 1 = 0x%02I64x%016I64x\n",
             j, i, ResultHighPart, ResultLowPart);
}
```

```Output
0x100000000000000001 << 1 = 0x200000000000000002
0x100000000000000001 >> 1 = 0x080000000000000000
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[__shiftright128](../intrinsics/shiftright128.md)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)