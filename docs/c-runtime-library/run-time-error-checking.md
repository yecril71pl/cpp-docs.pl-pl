---
title: Sprawdzanie błędów czasu wykonywania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.runtime
dev_langs:
- C++
helpviewer_keywords:
- run-time error checking
- run-time errors, checking
ms.assetid: c965dd01-57ad-4a3c-b1d6-5aa04f920501
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2468cd05efdf732fbf955b8532a61d24fa6c0ff4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="run-time-error-checking"></a>Sprawdzanie błędów czasu wykonywania

Biblioteki wykonawcze języka C zawiera funkcje, które obsługują sprawdzanie błędów czasu wykonywania (RTC). Sprawdzanie błędów czasu wykonywania umożliwia tworzenie programu w taki sposób, że niektóre rodzaje błędów czasu wykonywania są zgłaszane. Należy określić sposób zgłaszania błędów oraz jakie rodzaje błędy są zgłaszane. Aby uzyskać więcej informacji, zobacz [porady: Użyj natywnego Run-Time sprawdza](/visualstudio/debugger/how-to-use-native-run-time-checks).

 Aby dostosować sposób którą program obsługuje sprawdzanie błędów czasu wykonywania, należy użyć następujących funkcji.

## <a name="run-time-error-checking-functions"></a>Funkcje sprawdzanie błędów czasu wykonywania

|Funkcja|Zastosowanie|
|--------------|---------|
|[_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md)|Zwraca krótki opis typu sprawdzanie błędów czasu wykonywania.|
|[_RTC_NumErrors](../c-runtime-library/reference/rtc-numerrors.md)|Zwraca sumę błędów, które mogą być wykryte przez sprawdzanie błędów czasu wykonywania.|
|[_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md)|Określa funkcję jako program obsługi raportowania sprawdzanie błędów czasu wykonywania.|
|[_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md)|Kojarzy błąd, który jest wykrywany przez sprawdzanie błędów czasu wykonywania typu.|

## <a name="see-also"></a>Zobacz też

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
 [/RTC (Sprawdzanie błędów czasu wykonywania)](../build/reference/rtc-run-time-error-checks.md)<br/>
 [runtime_checks](../preprocessor/runtime-checks.md)<br/>
 [Procedury debugowania](../c-runtime-library/debug-routines.md)<br/>
