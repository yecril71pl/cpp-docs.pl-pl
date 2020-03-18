---
title: Sprawdzanie błędów czasu wykonywania
ms.date: 11/04/2016
helpviewer_keywords:
- run-time error checking
- run-time errors, checking
ms.assetid: c965dd01-57ad-4a3c-b1d6-5aa04f920501
ms.openlocfilehash: cf707cbd53e2285684d53d3f440db0f618343598
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444830"
---
# <a name="run-time-error-checking"></a>Sprawdzanie błędów czasu wykonywania

Biblioteka wykonawcza C zawiera funkcje, które obsługują sprawdzanie błędów czasu wykonywania (RTC). Sprawdzanie błędów czasu wykonywania umożliwia skompilowanie programu w taki sposób, że zgłaszane są pewne rodzaje błędów w czasie wykonywania. Określ sposób zgłaszania błędów oraz typy błędów, które są raportowane. Aby uzyskać więcej informacji, zobacz [jak: korzystanie z natywnych testów w czasie wykonywania](/visualstudio/debugger/how-to-use-native-run-time-checks).

Użyj następujących funkcji, aby dostosować sposób sprawdzania błędów w programie w czasie wykonywania.

## <a name="run-time-error-checking-functions"></a>Funkcje sprawdzania błędów czasu wykonywania

|Funkcja|Użycie|
|--------------|---------|
|[_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md)|Zwraca Krótki opis typu sprawdzania błędu czasu wykonywania.|
|[_RTC_NumErrors](../c-runtime-library/reference/rtc-numerrors.md)|Zwraca łączną liczbę błędów, które mogą zostać wykryte przez sprawdzanie błędów czasu wykonywania.|
|[_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md)|Określa funkcję jako procedurę obsługi do sprawdzania błędów czasu wykonywania raportowania.|
|[_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md)|Kojarzy błąd, który został wykryty przez sprawdzanie błędów czasu wykonywania z typem.|

## <a name="see-also"></a>Zobacz też

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[/RTC (Sprawdzanie błędów czasu wykonywania)](../build/reference/rtc-run-time-error-checks.md)<br/>
[runtime_checks](../preprocessor/runtime-checks.md)<br/>
[Procedury debugowania](../c-runtime-library/debug-routines.md)<br/>
