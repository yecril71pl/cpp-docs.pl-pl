---
title: _local_unwind2 — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _local_unwind2
apilocation:
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- _local_unwind2
- local_unwind2
dev_langs:
- C++
helpviewer_keywords:
- _local_unwind2 function
- local_unwind2 function
ms.assetid: 44f1fa82-e01e-490f-a6e6-18fc6811c28c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47227d4be0ad1c5145a9064d11b4ea633c7d7fc1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035789"
---
# <a name="localunwind2"></a>_local_unwind2

Wewnętrzny funkcji CRT. Uruchamia wszystkie programy obsługi przerwania, które są wymienione w tabeli wskazany zakres.

## <a name="syntax"></a>Składnia

```
void _local_unwind2(
   PEXCEPTION_REGISTRATION xr,
   int stop
);
```

#### <a name="parameters"></a>Parametry

*XR*<br/>
[in] Rekord rejestracji, który jest skojarzony z tabelą jeden zakres.

*Zatrzymaj*<br/>
[in] Poziom leksykalne, która wskazuje, gdzie `_local_unwind2` powinna zostać przerwana.

## <a name="remarks"></a>Uwagi

Ta metoda jest używana tylko w środowisku uruchomieniowym. Nie wywołuj metody w kodzie.

Ta metoda jest wykonywana programy obsługi zakończenia, uruchamia na bieżącym poziomie leksykalne i działa w drodze się leksykalne poziomów, aż do napotkania poziom jest wskazywany przez `stop`. Nie wykonuj programy obsługi zakończenia na poziomie, który jest wskazywany przez `stop`.

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)