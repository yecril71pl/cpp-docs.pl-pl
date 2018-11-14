---
title: _mm_stream_si64x
ms.date: 11/04/2016
f1_keywords:
- _mm_stream_si64x
helpviewer_keywords:
- movnti instruction
- _mm_stream_si64x intrinsic
ms.assetid: 114c2cd0-085f-41aa-846e-87bdd56c9ee7
ms.openlocfilehash: 11b289deeb2fd4aadf9b5d500a3379d8af26fbb9
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330440"
---
# <a name="mmstreamsi64x"></a>_mm_stream_si64x

**Microsoft Specific**

Generuje instrukcję MOVNTI. Zapisuje dane `Source` lokalizacji w pamięci określonej przez `Dest`, bez zanieczyszczenie pamięci podręcznych.

## <a name="syntax"></a>Składnia

```
void _mm_stream_si64x(
   __int64 * Dest,
   __int64 Source
);
```

#### <a name="parameters"></a>Parametry

*docelowy*<br/>
[out] Wskaźnik do lokalizację do zapisania danych źródłowych do.

*Źródło*<br/>
[in] Dane do zapisania.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`_mm_stream_si64x`|X64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

## <a name="example"></a>Przykład

```C
// _mm_stream_si64x.c
// processor: x64

#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_mm_stream_si64x)

int main()
{
    __int64 val = 0xFFFFFFFFFFFFI64;
    __int64 a[10];

    memset(a, 0, sizeof(a));
    _mm_stream_si64x(a+1, val);
    printf_s( "%I64x %I64x %I64x %I64x", a[0], a[1], a[2], a[3]);
}
```

```Output
0 ffffffffffff 0 0
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)