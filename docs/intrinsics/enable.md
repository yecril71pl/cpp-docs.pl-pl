---
title: _enable
ms.date: 11/04/2016
f1_keywords:
- _enable
- _enable_cpp
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
ms.openlocfilehash: 1d129db17b489972555efb0b5df2de52e01fa649
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631253"
---
# <a name="enable"></a>_enable

**Microsoft Specific**

Umożliwia przerwań.

## <a name="syntax"></a>Składnia

```
void _enable(void);
```

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`_enable`|x86, ARM, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

`_enable` powoduje, że procesor, która ma ustawienie flagi przerwania. Na x86 systemów, ta funkcja generuje Ustaw flagę przerwań (`sti`) instrukcji.

Ta funkcja jest dostępna tylko w trybie jądra. Jeśli używane w trybie użytkownika, zwracany jest wyjątek instrukcja uprzywilejowana.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)