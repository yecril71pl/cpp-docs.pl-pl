---
title: _disable
ms.date: 09/02/2019
f1_keywords:
- _disable_cpp
- _disable
helpviewer_keywords:
- _disable intrinsic
- rsm instruction
- disable intrinsic
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
ms.openlocfilehash: 94be850e1d494ff62df84922b46f28481be68314
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216816"
---
# <a name="_disable"></a>_disable

**Microsoft Specific**

Wyłącza przerwania.

## <a name="syntax"></a>Składnia

```C
void _disable(void);
```

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`_disable`|x86, ARM, x64, ARM64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

`_disable`instruuje procesor, aby wyczyścił flagę przerwania. W systemach x86 ta funkcja generuje instrukcję Clear Interrupt flag (`cli`).

Ta funkcja jest dostępna tylko w trybie jądra. W przypadku użycia w trybie użytkownika wyjątek uprzywilejowanych instrukcji jest zgłaszany w czasie wykonywania.

Na platformach ARM i ARM64 ta procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
