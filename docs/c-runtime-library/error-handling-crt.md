---
title: Obsługa błędów (CRT) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.errors
dev_langs:
- C++
helpviewer_keywords:
- error handling, C routines for
- logic errors
- error handling, library routines
- testing, for program errors
ms.assetid: 125ac697-9eb0-4152-a440-b7842f23d97f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f39fe3743c023bb0c4cb3130400e9bcb7b97db1b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704850"
---
# <a name="error-handling-crt"></a>Obsługa błędów (CRT)

Użyj tych procedur obsługi błędów programu.

## <a name="error-handling-routines"></a>Procedury obsługi błędów

|Procedura|Zastosowanie|
|-------------|---------|
|[Assert](../c-runtime-library/reference/assert-macro-assert-wassert.md) — makro|Testowanie programowania błędy logiczne; dostępne w wersji i debugowania wersja biblioteki wykonawczej.|
|[_ASSERT, _asserte —](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makra|Podobnie jak **assert**, ale są dostępne tylko w wersjach debugowania biblioteki czasu wykonywania.|
|[clearerr](../c-runtime-library/reference/clearerr.md)|Resetowanie wskaźnika błędów. Wywoływanie **rewind** lub zamykania strumienia również resetuje wskaźnik błędów.|
|[_eof](../c-runtime-library/reference/eof.md)|Sprawdź, czy koniec pliku w we/wy niskiego poziomu.|
|[feof](../c-runtime-library/reference/feof.md)|Test na końcu pliku. Koniec pliku jest również wskazane, gdy **_przeczytaj** zwraca wartość 0.|
|[ferror](../c-runtime-library/reference/ferror.md)|Sprawdź błędy We/Wy strumienia.|
|[_RPT, _RPTF](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) makra|Generowanie raportu, podobnie jak **printf**, ale są dostępne tylko w wersjach debugowania biblioteki czasu wykonywania.|
|[_set_error_mode](../c-runtime-library/reference/set-error-mode.md)|Modyfikuje **__error_mode** do określenia lokalizacji innych niż domyślne, gdzie C, czas wykonywania zapisuje komunikat o błędzie dla błędu, który prawdopodobnie będzie zakończyć program.|
|[_set_purecall_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)|Ustawia wywołanie czystej funkcji wirtualnej programu obsługi.|

## <a name="see-also"></a>Zobacz także

- [Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)
