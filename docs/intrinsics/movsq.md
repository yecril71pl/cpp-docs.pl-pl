---
title: __movsq
ms.date: 09/02/2019
f1_keywords:
- __movsq
helpviewer_keywords:
- __movsq intrinsic
- rep movsq instruction
- movsq instruction
ms.assetid: be116a6e-2176-4ca4-93b1-9ccf3e7e7835
ms.openlocfilehash: 66de1971c48f6697fd06579fac635cce31545e92
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217265"
---
# <a name="__movsq"></a>__movsq

**Microsoft Specific**

Generuje powtórzoną instrukcję przenoszenia ciągu`rep movsq`().

## <a name="syntax"></a>Składnia

```C
void __movsq(
   unsigned char* Destination,
   unsigned char* Source,
   size_t Count
);
```

### <a name="parameters"></a>Parametry

*Punktu*\
określoną Miejsce docelowe operacji.

*Zewnętrz*\
podczas Źródło operacji.

*Liczbą*\
podczas Liczba quadwords do skopiowania.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__movsq`|X64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Wynikiem tego jest to, że pierwsza *Liczba* quadwords wskazana przez *Źródło* jest kopiowana do ciągu *docelowego* .

Ta procedura jest dostępna tylko jako wewnętrzna.

## <a name="example"></a>Przykład

```cpp
// movsq.cpp
// processor: x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsq)

int main()
{
    unsigned __int64 a1[10];
    unsigned __int64 a2[10] = {950, 850, 750, 650, 550, 450, 350, 250,
                               150, 50};
    __movsq(a1, a2, 10);

    for (int i = 0; i < 10; i++)
       printf_s("%d ", a1[i]);
    printf_s("\n");
}
```

```Output
950 850 750 650 550 450 350 250 150 50
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
