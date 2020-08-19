---
title: __lidt
ms.date: 09/02/2019
f1_keywords:
- __lidt
- __lidt_cpp
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
ms.openlocfilehash: 87a49643e7cd11ae57dc01130f250895cf012065
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562496"
---
# <a name="__lidt"></a>__lidt

**Specyficzne dla firmy Microsoft**

Ładuje rejestr tabeli deskryptorów przerwań (IDTR) z wartością w określonej lokalizacji pamięci.

## <a name="syntax"></a>Składnia

```C
void __lidt(void * Source);
```

### <a name="parameters"></a>Parametry

*Zewnętrz*\
podczas Wskaźnik do wartości, która ma zostać skopiowana do IDTR.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__lidt`|x86, x64|

**Plik nagłówka**\<intrin.h>

## <a name="remarks"></a>Uwagi

`__lidt`Funkcja jest równoważna z `LIDT` instrukcją Machine i jest dostępna tylko w trybie jądra. Aby uzyskać więcej informacji, Wyszukaj dokument "Podręcznik Intel Architecture Software Developer, Tom 2: odwołanie do zestawu instrukcji" w witrynie [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[__sidt](../intrinsics/sidt.md)
