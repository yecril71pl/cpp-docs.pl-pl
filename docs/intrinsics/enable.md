---
title: _włącz | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _enable
- _enable_cpp
dev_langs:
- C++
helpviewer_keywords:
- enable intrinsic
- _enable intrinsic
- ssm instruction
ms.assetid: 8bee669b-6bd8-4e25-9383-bb7d57295b4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce3b59bc6665c4622078285a0c3b4b5011bc7d9b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433383"
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