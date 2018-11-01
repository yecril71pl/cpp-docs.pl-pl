---
title: Obsługa błędów (CRT)
ms.date: 11/04/2016
f1_keywords:
- c.errors
helpviewer_keywords:
- error handling, C routines for
- logic errors
- error handling, library routines
- testing, for program errors
ms.assetid: 125ac697-9eb0-4152-a440-b7842f23d97f
ms.openlocfilehash: 7b3a5676c9297b1d7805f92b3a15cc71518ecd65
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551222"
---
# <a name="error-handling-crt"></a>Obsługa błędów (CRT)

Użyj tych procedur, aby obsługiwać błędy programu.

## <a name="error-handling-routines"></a>Procedury obsługi błędów

|Procedura|Zastosowanie|
|-------------|---------|
|[asercja](../c-runtime-library/reference/assert-macro-assert-wassert.md) — makro|Test dla programowania błędy logiczne; dostępne w wersji wydania i debugowe wersji biblioteki wykonawczej.|
|[_ASSERT, _asserte —](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makra|Podobnie jak **asercja**, ale jest dostępna tylko w wersji debugowania bibliotek wykonawczych.|
|[clearerr](../c-runtime-library/reference/clearerr.md)|Resetowanie wskaźnika błędów. Wywoływanie **rewind** lub zamyka strumień również resetuje wskaźnik błędu.|
|[_eof](../c-runtime-library/reference/eof.md)|Sprawdź, czy koniec pliku operacji We/Wy niskiego poziomu.|
|[feof](../c-runtime-library/reference/feof.md)|Test na końcu pliku. Koniec pliku jest również wskazane, gdy **_przeczytaj** zwraca wartość 0.|
|[ferror](../c-runtime-library/reference/ferror.md)|Sprawdź błędy We/Wy strumienia.|
|[_RPT, _RPTF](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) makra|Generowanie raportu, podobnie jak **printf**, ale jest dostępna tylko w wersji debugowania bibliotek wykonawczych.|
|[_set_error_mode](../c-runtime-library/reference/set-error-mode.md)|Modyfikuje **__error_mode** do określenia lokalizacji innej niż domyślna, w którym C, czas wykonywania zapisuje komunikat o błędzie Wystąpił błąd prawdopodobnie zakończy się program.|
|[_set_purecall_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)|Ustawia element obsługujący dla wywołania czystą funkcję wirtualną.|

## <a name="see-also"></a>Zobacz także

- [Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)
