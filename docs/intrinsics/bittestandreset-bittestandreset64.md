---
title: _bittestandreset, _bittestandreset64
ms.date: 09/02/2019
f1_keywords:
- _bittestandreset64_cpp
- _bittestandreset
- _bittestandreset_cpp
- _bittestandreset64
helpviewer_keywords:
- btr instruction
- _bittestandreset intrinsic
- _bittestandreset64 intrinsic
ms.assetid: 8dad63bb-a051-4cd7-a793-3357537dfeaf
ms.openlocfilehash: 9e0c869b926b2f9f3c04fd648f84ef33b8d16fcd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216922"
---
# <a name="_bittestandreset-_bittestandreset64"></a>_bittestandreset, _bittestandreset64

**Microsoft Specific**

Wygeneruj instrukcję, aby przeanalizować `b` bit `a`adresu, zwrócić jego bieżącą wartość i zresetować bit do wartości 0.

## <a name="syntax"></a>Składnia

```C
unsigned char _bittestandreset(
   long *a,
   long b
);
unsigned char _bittestandreset64(
   __int64 *a,
   __int64 b
);
```

### <a name="parameters"></a>Parametry

*z*\
[in. out] Wskaźnik do pamięci do sprawdzenia.

*b*\
podczas Pozycja bitu do przetestowania.

## <a name="return-value"></a>Wartość zwracana

Bit w określonym położeniu.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`_bittestandreset`|x86, ARM, x64, ARM64|
|`_bittestandreset64`|x64, ARM64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna tylko jako wewnętrzna.

## <a name="example"></a>Przykład

```cpp
// bittestandreset.cpp
// processor: x86, IPF, x64
#include <stdio.h>
#include <limits.h>
#include <intrin.h>

#pragma intrinsic(_bittestandreset)

// Check the sign bit and reset to 0 (taking the absolute value)
// Returns 0 if the number is positive or zero
// Returns 1 if the number is negative
unsigned char absolute_value(long* p)
{
   const int SIGN_BIT = 31;
   return _bittestandreset(p, SIGN_BIT);
}

int main()
{
    long i = -112;
    unsigned char result;

    // Check the sign bit and reset to 0 (taking the absolute value)

    result = absolute_value(&i);
    if (result == 1)
        printf_s("The number was negative.\n");
}
```

```Output
The number was negative.
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
