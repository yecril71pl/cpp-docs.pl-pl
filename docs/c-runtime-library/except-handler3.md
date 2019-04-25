---
title: _except_handler3
ms.date: 11/04/2016
apiname:
- _except_handler3
apilocation:
- msvcrt.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- _except_handler3
- except_handler3
helpviewer_keywords:
- _except_handler3 function
- except_handler3 function
ms.assetid: b0c64898-0ae5-48b7-9724-80135a0813e2
ms.openlocfilehash: 0dfe007d7b444401accbf547674f96f7f7d54ac1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62289961"
---
# <a name="excepthandler3"></a>_except_handler3

Wewnętrzny funkcji CRT. Używane przez platformę, można znaleźć odpowiedni wyjątek program obsługi przetwarzał bieżący wyjątek.

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
[in] Informacje na temat określonego wyjątku.

*Rejestracja*<br/>
[in] Rekord, który wskazuje zakres tabeli, która powinna być używana, można znaleźć programu obsługi wyjątków.

*Kontekst*<br/>
[in] Zastrzeżone.

*dispatcher*<br/>
[in] Zastrzeżone.

## <a name="return-value"></a>Wartość zwracana

Jeśli wyjątek powinien zostać odwołany, zwraca `DISPOSITION_DISMISS`. Jeśli wyjątek powinien zostać przekazany w górę o jeden poziom, do hermetyzowany obsługi wyjątków, zwraca `DISPOSITION_CONTINUE_SEARCH`.

## <a name="remarks"></a>Uwagi

Jeśli ta metoda umożliwia znalezienie obsługi wyjątków odpowiednie, przekazuje wyjątek do programu obsługi. W takiej sytuacji ta metoda nie zwraca do kodu, który ją wywołuje, i wartość zwracana jest bez znaczenia.

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)
