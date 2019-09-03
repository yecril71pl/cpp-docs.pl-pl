---
title: __stosb
ms.date: 09/02/2019
f1_keywords:
- __stosb
helpviewer_keywords:
- rep stosb instruction
- __stosb intrinsic
- stosb instruction
ms.assetid: 634589ed-2da3-439b-a381-a214d89bf10c
ms.openlocfilehash: edf74da4c8b5aa97e542d89f55b3ed8411db9bac
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221215"
---
# <a name="__stosb"></a>__stosb

**Microsoft Specific**

Generuje instrukcję ciągu magazynu (`rep stosb`).

## <a name="syntax"></a>Składnia

```C
void __stosb(
   unsigned char* Destination,
   unsigned char Data,
   size_t Count
);
```

### <a name="parameters"></a>Parametry

*Punktu*\
określoną Miejsce docelowe operacji.

*Data*\
podczas Dane do zapisania.

*Liczbą*\
podczas Długość bloku bajtów do zapisania.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__stosb`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Wynik polega na tym, że *dane* znakowe są zapisywane w bloku *Count* bajtów w ciągu *docelowym* .

Ta procedura jest dostępna tylko jako wewnętrzna.

## <a name="example"></a>Przykład

```C
// stosb.c
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__stosb)

int main()
{
    unsigned char c = 0x40; /* '@' character */
    unsigned char s[] = "*********************************";

    printf_s("%s\n", s);
    __stosb((unsigned char*)s+1, c, 6);
    printf_s("%s\n", s);

}
```

```Output
*********************************
*@@@@@@**************************
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
