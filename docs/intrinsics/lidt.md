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
ms.openlocfilehash: 24778b761ada56830b155a2fc65e90f54ba729ed
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217510"
---
# <a name="__lidt"></a>__lidt

**Microsoft Specific**

Ładuje rejestr tabeli deskryptorów przerwań (IDTR) z wartością w określonej lokalizacji pamięci.

## <a name="syntax"></a>Składnia

```C
void __lidt(void * Source);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Element źródłowy*|podczas Wskaźnik do wartości, która ma zostać skopiowana do IDTR.|

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__lidt`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Funkcja jest równoważna `LIDT` z instrukcją Machine i jest dostępna tylko w trybie jądra. `__lidt` Aby uzyskać więcej informacji, Wyszukaj dokument "Podręcznik Intel Architecture Developer, Tom 2: Odwołanie do zestawu instrukcji "w witrynie [firmy Intel Corporation](https://software.intel.com/articles/intel-sdm) .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[__sidt](../intrinsics/sidt.md)
