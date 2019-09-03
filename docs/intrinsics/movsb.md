---
title: __movsb
ms.date: 09/02/2019
f1_keywords:
- __movsb
helpviewer_keywords:
- movsb instruction
- rep movsb instruction
- __movsb intrinsic
ms.assetid: ba5469f6-f797-4cd2-bee8-74c7666c26d4
ms.openlocfilehash: ca06fc9114f6e824a690cc4e612c21d705a485cd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217282"
---
# <a name="__movsb"></a>__movsb

**Microsoft Specific**

Generuje instrukcję Move String (`rep movsb`).

## <a name="syntax"></a>Składnia

```C
void __movsb(
   unsigned char* Destination,
   unsigned const char* Source,
   size_t Count
);
```

### <a name="parameters"></a>Parametry

*Punktu*\
określoną Wskaźnik do lokalizacji docelowej kopii.

*Zewnętrz*\
podczas Wskaźnik do źródła kopii.

*Liczbą*\
podczas Liczba bajtów do skopiowania.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__movsb`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

W efekcie pierwsze `Count` bajty wskazywane przez `Source` są kopiowane do `Destination` ciągu.

Ta procedura jest dostępna tylko jako wewnętrzna.

## <a name="example"></a>Przykład

```cpp
// movsb.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsb)

int main()
{
    unsigned char s1[100];
    unsigned char s2[100] = "A big black dog.";
    __movsb(s1, s2, 100);

    printf_s("%s %s", s1, s2);
}
```

```Output
A big black dog. A big black dog.
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
