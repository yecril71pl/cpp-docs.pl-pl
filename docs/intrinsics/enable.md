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
ms.openlocfilehash: e1ece6d6f4040b81b55d8400407d46f165b56b53
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349033"
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

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)