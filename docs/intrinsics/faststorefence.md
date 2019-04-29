---
title: __faststorefence
ms.date: 11/04/2016
f1_keywords:
- __faststorefence_cpp
- __faststorefence
helpviewer_keywords:
- __faststorefence intrinsic
- sfence instruction
ms.assetid: 6c6eb973-3cf0-4306-b3af-cfde9b0210a5
ms.openlocfilehash: a0c8027f443a475b03521920e2e036e7ed4eaafb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349007"
---
# <a name="faststorefence"></a>__faststorefence

**Microsoft Specific**

Gwarancje, co poprzednie odwołanie do pamięci, tym ładowania i przechowywania w przypadku odwołania do pamięci jest widoczne globalnie przed dowolnego odwołania do kolejnych pamięci.

## <a name="syntax"></a>Składnia

```
void __faststorefence();
```

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__faststorefence`|X64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Generuje sekwencję instrukcji barierę całej pamięci czy gwarancje ładowania i przechowywania operacje wydane przed tym wewnętrzne są globalnie nadal widoczne przed wykonaniem. Efekt jest porównywalna do, ale szybciej niż `_mm_mfence` wewnętrzne na x64 wszystkich platform.

Na platformie AMD64, ta procedura generuje instrukcji, która jest ogrodzeniem magazynu szybciej niż `sfence` instrukcji. Dla kodu wrażliwego na czas, użyj tym wewnętrzne zamiast `_mm_sfence` tylko na platformach AMD64. Na platformach firmy Intel x64 `_mm_sfence` instrukcji jest szybsze.

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)