---
title: _except_handler3
ms.date: 11/04/2016
api_name:
- _except_handler3
api_location:
- msvcrt.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _except_handler3
- except_handler3
helpviewer_keywords:
- _except_handler3 function
- except_handler3 function
ms.assetid: b0c64898-0ae5-48b7-9724-80135a0813e2
ms.openlocfilehash: 5e1dbab97e0f193d4ff59c19229d2c00e2cd7d6a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944482"
---
# <a name="_except_handler3"></a>_except_handler3

Wewnętrzna funkcja CRT. Używane przez platformę do znajdowania odpowiedniego programu obsługi wyjątków w celu przetworzenia bieżącego wyjątku.

## <a name="syntax"></a>Składnia

```
int _except_handler3(
   PEXCEPTION_RECORD exception_record,
   PEXCEPTION_REGISTRATION registration,
   PCONTEXT context,
   PEXCEPTION_REGISTRATION dispatcher
);
```

#### <a name="parameters"></a>Parametry

*exception_record*<br/>
podczas Informacje o konkretnym wyjątku.

*zarejestrowany*<br/>
podczas Rekord wskazujący, która tabela zakresu powinna być używana do znajdowania programu obsługi wyjątków.

*Context*<br/>
podczas Rezerwacj.

*dispatcher*<br/>
podczas Rezerwacj.

## <a name="return-value"></a>Wartość zwracana

Jeśli wyjątek powinien zostać odrzucony, zwraca `DISPOSITION_DISMISS`. Jeśli do wyjątku należy przekazywać poziom do obsługi wyjątków hermetyzowania, zwraca `DISPOSITION_CONTINUE_SEARCH`.

## <a name="remarks"></a>Uwagi

Jeśli ta metoda znajdzie odpowiednią procedurę obsługi wyjątków, przekazuje wyjątek do procedury obsługi. W tej sytuacji ta metoda nie zwraca do kodu, który go wywołał, a zwracana wartość nie jest istotna.

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)
