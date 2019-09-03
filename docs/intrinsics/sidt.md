---
title: __sidt
ms.date: 09/02/2019
f1_keywords:
- __sidt
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
ms.openlocfilehash: d6b685da0e02373307a3149c5b7b28213f37ad40
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222324"
---
# <a name="__sidt"></a>__sidt

**Microsoft Specific**

Przechowuje wartość rejestru tabeli deskryptorów przerwań (IDTR) w określonej lokalizacji pamięci.

## <a name="syntax"></a>Składnia

```C
void __sidt(void * Destination);
```

### <a name="parameters"></a>Parametry

*Punktu*\
podczas Wskaźnik do lokalizacji pamięci, w której jest przechowywany IDTR.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__sidt`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Funkcja jest równoważna `SIDT` z instrukcją maszyny. `__sidt` Aby uzyskać więcej informacji, Wyszukaj dokument "Podręcznik Intel Architecture Developer, Tom 2: Odwołanie do zestawu instrukcji "w witrynie [firmy Intel Corporation](https://software.intel.com/articles/intel-sdm) .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[__lidt](../intrinsics/lidt.md)
