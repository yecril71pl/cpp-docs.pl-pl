---
title: __getcallerseflags
ms.date: 11/04/2016
f1_keywords:
- _getcallerseflags
- _getcallerseflags_cpp
helpviewer_keywords:
- _getcallerseflags intrinsic
ms.assetid: 2386596f-33aa-4cc7-b026-5a834637270a
ms.openlocfilehash: a2df7087c605882340da16f56dae2e991c5d7dd1
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039942"
---
# <a name="getcallerseflags"></a>__getcallerseflags

**Specyficzne dla firmy Microsoft**

Zwraca wartość EFLAGS kontekst obiektu wywołującego.

## <a name="syntax"></a>Składnia

```
unsigned int __getcallerseflags(void);
```

## <a name="return-value"></a>Wartość zwracana

Wartość EFLAGS z kontekstu obiektu wywołującego.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__getcallerseflags`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

## <a name="example"></a>Przykład

```
// getcallerseflags.cpp
// processor: x86, x64

#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__getcallerseflags)

unsigned int g()
{
    unsigned int EFLAGS = __getcallerseflags();
    printf_s("EFLAGS 0x%x\n", EFLAGS);
    return EFLAGS;
}
unsigned int f()
{
    return g();
}

int main()
{
    unsigned int i;
    i = f();
    i = g();
    return 0;
}
```

```Output
EFLAGS 0x202
EFLAGS 0x206
```

**KONIEC Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)