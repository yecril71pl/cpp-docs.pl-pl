---
title: __stosq
ms.date: 11/04/2016
f1_keywords:
- __stosq
helpviewer_keywords:
- rep stosq instruction
- stosq instruction
- __stosq intrinsic
ms.assetid: 3ea28297-4369-4c2d-bf0c-91fa539ce209
ms.openlocfilehash: 48c3e8db2683ee190a23974d12d36fbeef6a0094
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477470"
---
# <a name="stosq"></a>__stosq

**Microsoft Specific**

Generuje instrukcję ciągu magazynu (`rep stosq`).

## <a name="syntax"></a>Składnia

```
void __stosb( 
   unsigned __int64* Dest, 
   unsigned __int64 Data, 
   size_t Count 
);
```

#### <a name="parameters"></a>Parametry

*docelowy*<br/>
[out] Lokalizacja docelowa wykonać operację.

*Dane*<br/>
[in] Dane, które mają być przechowywane.

*Liczba*<br/>
[in] Długość bloku wyrazy w liczbie mnogiej do zapisania.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__stosq`|AMD64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Wynik jest fakt, że quadword `Data` są zapisywane w bloku `Count` wyrazy w liczbie mnogiej w `Dest` ciągu.

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

## <a name="example"></a>Przykład

```
// stosq.c
// processor: x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__stosq)

int main()
{
   unsigned __int64 val = 0xFFFFFFFFFFFFI64;
   unsigned __int64 a[10];
   memset(a, 0, sizeof(a));
   __stosq(a+1, val, 2);
   printf("%I64x %I64x %I64x %I64x", a[0], a[1], a[2], a[3]);
}
```

## <a name="output"></a>Dane wyjściowe

```
0 ffffffffffff ffffffffffff 0
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)