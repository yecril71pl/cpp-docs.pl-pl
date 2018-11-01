---
title: Sprawdzanie błędów czasu wykonywania
ms.date: 11/04/2016
f1_keywords:
- c.runtime
helpviewer_keywords:
- run-time error checking
- run-time errors, checking
ms.assetid: c965dd01-57ad-4a3c-b1d6-5aa04f920501
ms.openlocfilehash: 348698faa1f91e4d98acc762538fc1cbdb798e0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435650"
---
# <a name="run-time-error-checking"></a>Sprawdzanie błędów czasu wykonywania

Biblioteki wykonawczej C zawiera funkcje, które obsługują sprawdzanie błędów czasu wykonywania (RTC). Sprawdzanie błędów czasu wykonywania pozwala na tworzenie programu w taki sposób, że niektóre rodzaje błędów czasu wykonywania są zgłaszane. Należy określić sposób zgłaszania błędów i jakie rodzaje błędy są zgłaszane. Aby uzyskać więcej informacji, zobacz [porady: użycie macierzystego sprawdzania w trakcie wykonywania](/visualstudio/debugger/how-to-use-native-run-time-checks).

Należy użyć następujących funkcji, aby dostosować sposób, w jaki program obsługuje sprawdzanie błędów czasu wykonywania.

## <a name="run-time-error-checking-functions"></a>Błąd w czasie wykonywania sprawdzania funkcji

|Funkcja|Zastosowanie|
|--------------|---------|
|[_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md)|Zwraca krótki opis typu sprawdzanie błędów czasu wykonywania.|
|[_RTC_NumErrors](../c-runtime-library/reference/rtc-numerrors.md)|Zwraca całkowitą liczbę błędów, które mogą być wykryte przez sprawdzanie błędów czasu wykonywania.|
|[_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md)|Określa funkcję jako program obsługi raportowania sprawdzanie błędów czasu wykonywania.|
|[_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md)|Kojarzy błąd, który zostanie wykryty przez sprawdzanie błędów czasu wykonywania o typie.|

## <a name="see-also"></a>Zobacz też

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[/RTC (Sprawdzanie błędów czasu wykonywania)](../build/reference/rtc-run-time-error-checks.md)<br/>
[runtime_checks](../preprocessor/runtime-checks.md)<br/>
[Procedury debugowania](../c-runtime-library/debug-routines.md)<br/>
