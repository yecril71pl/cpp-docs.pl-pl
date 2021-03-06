---
title: Obsługa wyjątków — Procedury
ms.date: 11/04/2016
f1_keywords:
- c.exceptions
helpviewer_keywords:
- exception handling, routines
ms.assetid: f60548c6-850a-4e1e-a79b-a2a6a541ab62
ms.openlocfilehash: 8def356793906074e6fc4b8d7a139ce1915a5f9b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344307"
---
# <a name="exception-handling-routines"></a>Obsługa wyjątków — Procedury

Użyj funkcji obsługi wyjątków języka C++, aby odzyskać z nieoczekiwanych zdarzeń podczas wykonywania programu.

## <a name="exception-handling-functions"></a>Funkcje obsługi wyjątków

|Funkcja|Zastosowanie|
|--------------|---------|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Win32 obsługi wyjątków (wyjątki strukturalne C), co kod C++ wpisane wyjątków|
|[set_terminate](../c-runtime-library/reference/set-terminate-crt.md)|Zainstaluj własną procedurę kończenia żądań ma zostać wywołana przez **zakończenia**|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Zainstaluj własną funkcję zakończenia ma zostać wywołana przez **nieoczekiwany**|
|[Zakończenie](../c-runtime-library/reference/terminate-crt.md)|Wywołuje się automatycznie w pewnych okolicznościach po wyrzuceniu wyjątku. **Zakończyć** wywołaniach funkcji **przerwać** funkcji można określić za pomocą **set_terminate**|
|[unexpected](../c-runtime-library/reference/unexpected-crt.md)|Wywołania **zakończyć** funkcji można określić za pomocą **set_unexpected**. **Nieoczekiwany** funkcja nie jest używany w bieżącej implementacji obsługi wyjątków C++ firmy Microsoft|

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
