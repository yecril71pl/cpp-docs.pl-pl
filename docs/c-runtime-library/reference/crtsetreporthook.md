---
title: _Crtsetreporthook — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtSetReportHook
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _CrtSetReportHook
- CrtSetReportHook
dev_langs:
- C++
helpviewer_keywords:
- CrtSetReportHook function
- _CrtSetReportHook function
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ef76fe0b7befb99b5bf0e8bb69fa1a1229782de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="crtsetreporthook"></a>_CrtSetReportHook

Instaluje zdefiniowane przez klienta funkcji raportowania przez Przechwytywanie go do procesu raportowania debugowania środowiska wykonawczego C (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
_CRT_REPORT_HOOK _CrtSetReportHook(
   _CRT_REPORT_HOOK reportHook
);
```

### <a name="parameters"></a>Parametry

*reportHook*<br/>
Nowy klient funkcji zdefiniowanej przez raportowania do przyłączanie się do C-run-time debugowania procesu raportowania.

## <a name="return-value"></a>Wartość zwracana

Zwraca poprzedni klienta zdefiniowanych funkcji raportowania.

## <a name="remarks"></a>Uwagi

**_Crtsetreporthook —** pozwala aplikacji na używanie własnej raportowania funkcji do biblioteki wykonawcze debugowania C raportowania procesu. W związku z tym, gdy [_crtdbgreport —](crtdbgreport-crtdbgreportw.md) jest nazywany aby wygenerować raport debugowania, raportowanie do aplikacji, funkcja jest wywoływana, najpierw. Ta funkcja umożliwia wykonywanie operacji takich jak filtrowania raportów debugowania można skupić się na typy alokacji określonych lub wysłać raport do miejsc docelowych nie jest dostępny za pomocą aplikacji **_crtdbgreport —**. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań **_crtsetreporthook —** są usuwane podczas przetwarzania wstępnego.

Bardziej niezawodna w wersji **_crtsetreporthook —**, zobacz [_crtsetreporthook2 —](crtsetreporthook2-crtsetreporthookw2.md).

**_Crtsetreporthook —** funkcja instaluje nowy klient zdefiniowane przez określone w funkcji raportowania *reportHook* i zwraca poprzedniego punktu zaczepienia zdefiniowane przez klienta. W poniższym przykładzie pokazano, jak powinna być prototypowana haku zdefiniowane przez klienta raportu:

```C
int YourReportHook( int reportType, char *message, int *returnValue );
```

gdzie *reportType* jest typ raportu debugowania (**_CRT_WARN**, **_CRT_ERROR**, lub **_CRT_ASSERT**), *komunikat* jest całkowicie złożony debugowania komunikat użytkownika mają być zawarte w raporcie, i **returnValue** jest wartość określoną przez klienta zdefiniowane raportowania funkcji, która ma zostać zwrócony przez **_ Crtdbgreport —**. Pełny opis typy dostępnych raportów, zobacz [_crtsetreportmode —](crtsetreportmode.md) funkcji.

Jeśli funkcja raportowania zdefiniowana przez klienta obsługuje całkowicie wiadomość debugowania taki sposób, że nie dalsze reporting jest wymagane, funkcja powinna zwrócić **TRUE**. Gdy funkcja zwraca **FALSE**, **_crtdbgreport —** jest wywoływana w celu wygenerowania raportu debugowania przy użyciu bieżących ustawień typ raportu, tryb i plików. Ponadto, określając **_crtdbgreport —** zwracają wartość w **returnValue**, aplikację można też kontrolować, czy występuje przerwanie debugowania. Pełny opis sposobu skonfigurowane i wygenerowany raport debugowania, zobacz **_crtsetreportmode —**, [_crtsetreportfile —](crtsetreportfile.md), i **_crtdbgreport —**.

Aby uzyskać więcej informacji na temat korzystania innych obsługą punktu zaczepienia funkcji środowiska wykonawczego i pisanie własnych klienta zdefiniowane przez funkcje punktów zaczepienia, zobacz [debugowania pisanie funkcji punktów zaczepienia](/visualstudio/debugger/debug-hook-function-writing).

> [!NOTE]
> Jeśli aplikacja jest skompilowana przy użyciu **/CLR** i funkcji raportowania jest wywoływana po zakończył działanie aplikacji głównej, CLR spowoduje zgłoszenie wyjątku, jeśli wszystkie funkcje CRT wywołuje funkcję raportowania.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtSetReportHook**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetReportHook](crtgetreporthook.md)<br/>
