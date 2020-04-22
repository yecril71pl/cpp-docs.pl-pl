---
title: _local_unwind2
ms.date: 11/04/2016
api_name:
- _local_unwind2
api_location:
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _local_unwind2
- local_unwind2
helpviewer_keywords:
- _local_unwind2 function
- local_unwind2 function
ms.assetid: 44f1fa82-e01e-490f-a6e6-18fc6811c28c
ms.openlocfilehash: cbcc0c6177ba4cc449daf6a385a7cce53b8c1230
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745328"
---
# <a name="_local_unwind2"></a>_local_unwind2

Wewnętrzna funkcja CRT. Uruchamia wszystkie programy obsługi zakończenia, które są wymienione we wskazanej tabeli zakresu.

## <a name="syntax"></a>Składnia

```cpp
void _local_unwind2(
   PEXCEPTION_REGISTRATION xr,
   int stop
);
```

#### <a name="parameters"></a>Parametry

*Xr*<br/>
[w] Rekord rejestracji skojarzony z jedną tabelą zakresu.

*Zatrzymać*<br/>
[w] Poziom leksykalny, `_local_unwind2` który wskazuje, gdzie należy się zatrzymać.

## <a name="remarks"></a>Uwagi

Ta metoda jest używana tylko przez środowisko czasu wykonywania. Nie należy wywoływać metody w kodzie.

Gdy ta metoda wykonuje programy obsługi zakończenia, rozpoczyna się na bieżącym poziomie leksykalnym i działa na poziomie leksykalnym, dopóki nie osiągnie poziomu, który jest wskazany przez `stop`. Nie wykonuje obsługi zakończenia na poziomie, który `stop`jest wskazany przez .

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)
