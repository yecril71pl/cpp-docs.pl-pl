---
title: _disable
ms.date: 11/04/2016
f1_keywords:
- _disable_cpp
- _disable
helpviewer_keywords:
- _disable intrinsic
- rsm instruction
- disable intrinsic
ms.assetid: 52da3df9-815c-4524-9839-6d1742cff5c6
ms.openlocfilehash: 93db063c6b53f0bec739ba134728b83379a21f53
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62264169"
---
# <a name="disable"></a>_disable

**Microsoft Specific**

Wyłącza przerwań.

## <a name="syntax"></a>Składnia

```
void _disable(void);
```

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`_disable`|x86, ARM, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

`_disable` powoduje, że procesora, aby wyczyścić flagę przerwania. Na x86 systemów, ta funkcja generuje Wyczyść flagę przerwań (`cli`) instrukcji.

Ta funkcja jest dostępna tylko w trybie jądra. Jeśli używane w trybie użytkownika, instrukcja uprzywilejowana jest wyjątek w czasie wykonywania.

Na platformach ARM, ta procedura jest dostępna wyłącznie jako wewnętrzna.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)