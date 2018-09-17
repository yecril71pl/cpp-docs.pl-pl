---
title: __stosb | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __stosb
dev_langs:
- C++
helpviewer_keywords:
- rep stosb instruction
- __stosb intrinsic
- stosb instruction
ms.assetid: 634589ed-2da3-439b-a381-a214d89bf10c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6a685633b6e23a21d46ad3256188fea3ee16ccc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700782"
---
# <a name="stosb"></a>__stosb

**Microsoft Specific**

Generuje instrukcję ciągu magazynu (`rep stosb`).

## <a name="syntax"></a>Składnia

```
void __stosb(
   unsigned char* Dest,
   unsigned char Data,
   size_t Count
);
```

#### <a name="parameters"></a>Parametry

*docelowy*<br/>
[out] Lokalizacja docelowa wykonać operację.

*Dane*<br/>
[in] Dane, które mają być przechowywane.

*Liczba*<br/>
[in] Długość bloku bajtów do zapisania.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__stosb`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Wynik jest to, że znak `Data` są zapisywane w bloku `Count` bajtów w `Dest` ciągu.

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

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

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)