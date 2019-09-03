---
title: __faststorefence
ms.date: 09/02/2019
f1_keywords:
- __faststorefence_cpp
- __faststorefence
helpviewer_keywords:
- __faststorefence intrinsic
- sfence instruction
ms.assetid: 6c6eb973-3cf0-4306-b3af-cfde9b0210a5
ms.openlocfilehash: d11a20666612fe1bca22f5d46b93e898dae375f6
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222176"
---
# <a name="__faststorefence"></a>__faststorefence

**Microsoft Specific**

Gwarantuje, że każde poprzednie odwołanie do pamięci, łącznie z odwołaniami do pamięci ładowania i zapisu, jest widoczne globalnie przed wszelkimi kolejnymi odwołaniami do pamięci.

## <a name="syntax"></a>Składnia

```C
void __faststorefence();
```

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__faststorefence`|X64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Generuje pełną sekwencję instrukcji z barierą pamięci, która gwarantuje, że operacje ładowania i przechowywania są wydawane przed kontynuowaniem wykonywania. Efekt jest porównywalny z szybkością, `_mm_mfence` ale większą niż wewnętrzna na wszystkich platformach x64.

Na platformie amd64 ta procedura generuje instrukcję, która jest szybszym ogrodzeniem magazynu niż `sfence` instrukcja. W przypadku kodu o kluczowym znaczeniu należy używać tego wewnętrznego `_mm_sfence` zamiast tylko na platformach amd64. Na platformach `_mm_sfence` Intel x64 instrukcje są szybsze.

Ta procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
