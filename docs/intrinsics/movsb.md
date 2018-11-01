---
title: __movsb
ms.date: 11/04/2016
f1_keywords:
- __movsb
helpviewer_keywords:
- movsb instruction
- rep movsb instruction
- __movsb intrinsic
ms.assetid: ba5469f6-f797-4cd2-bee8-74c7666c26d4
ms.openlocfilehash: 4b68eb4ca735274243db0c9ae006aa04be55355f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666937"
---
# <a name="movsb"></a>__movsb

**Microsoft Specific**

Generuje ciąg Przenieś (`rep movsb`) instrukcji.

## <a name="syntax"></a>Składnia

```
void __movsb( 
   unsigned char* Destination, 
   unsigned const char* Source, 
   size_t Count 
);
```

#### <a name="parameters"></a>Parametry

*miejsce docelowe*<br/>
[out] Wskaźnik do miejsca docelowego kopii.

*Źródło*<br/>
[in] Wskaźnik do źródła kopii.

*Liczba*<br/>
[in] Liczba bajtów do skopiowania.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__movsb`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

W wyniku pierwsze `Count` bajtów wskazywany przez `Source` są kopiowane do `Destination` ciągu.

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

## <a name="example"></a>Przykład

```
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

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)