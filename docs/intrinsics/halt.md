---
title: __halt
ms.date: 11/04/2016
f1_keywords:
- __halt
- __halt_cpp
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
ms.openlocfilehash: dd68c88a13035ca25f89304bcd84267a73978420
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025954"
---
# <a name="halt"></a>__halt

**Specyficzne dla firmy Microsoft**

Zatrzymuje procesor, dopóki nie wystąpi włączonych przerwania, nonmaskable przerwania (NMI) lub resetowania.

## <a name="syntax"></a>Składnia

```
void __halt( void );
```

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__halt`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

`__halt` Funkcji jest odpowiednikiem `HLT` komputera instrukcji i jest dostępna tylko w trybie jądra. Aby uzyskać więcej informacji, wyszukaj dokumentu, "Manual deweloper oprogramowania architekturze firmy Intel, wolumin 2: Instrukcja Ustaw odwołanie,"w [Intel Corporation](https://software.intel.com/articles/intel-sdm) lokacji.

**KONIEC Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)