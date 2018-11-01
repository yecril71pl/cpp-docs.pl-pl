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
ms.openlocfilehash: d99a87b1f3fd70d1fffb724629e9acded025732a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617181"
---
# <a name="halt"></a>__halt

**Microsoft Specific**

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

`__halt` Funkcji jest odpowiednikiem `HLT` komputera instrukcji i jest dostępna tylko w trybie jądra. Aby uzyskać więcej informacji, Wyszukaj w dokumencie "ręcznego deweloper oprogramowania architekturze firmy Intel, wolumin 2: odwołania do zestawu instrukcji," w [Intel Corporation](https://software.intel.com/articles/intel-sdm) lokacji.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)