---
title: __stosw
ms.date: 11/04/2016
f1_keywords:
- __stosw
helpviewer_keywords:
- stosw instruction
- __stosw intrinsic
- rep stosw instruction
ms.assetid: 7620fd1d-dba5-40e3-8e07-01aa68895133
ms.openlocfilehash: 4bfdf2191a4bf88ce6d061e1729e194236564330
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326423"
---
# <a name="stosw"></a>__stosw

**Microsoft Specific**

Generuje instrukcję ciągu magazynu (`rep stosw`).

## <a name="syntax"></a>Składnia

```
void __stosw(
   unsigned short* Dest,
   unsigned short Data,
   size_t Count
);
```

#### <a name="parameters"></a>Parametry

*docelowy*<br/>
[out] Lokalizacja docelowa wykonać operację.

*Dane*<br/>
[in] Dane, które mają być przechowywane.

*Liczba*<br/>
[in] Długość bloku słowa do zapisu.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__stosw`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Wynik jest to, że wyraz `Data` są zapisywane w bloku `Count` wyrazów w `Dest` ciągu.

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

## <a name="example"></a>Przykład

```
// stosw.c
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__stosw)

int main()
{
    unsigned short val = 128;
    unsigned short a[100];
    memset(a, 0, sizeof(a));
    __stosw(a+10, val, 2);
    printf_s("%u %u %u %u", a[9], a[10], a[11], a[12]);
}
```

```Output
0 128 128 0
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)