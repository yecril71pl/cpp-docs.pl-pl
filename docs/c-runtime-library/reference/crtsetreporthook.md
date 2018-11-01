---
title: _CrtSetReportHook
ms.date: 11/04/2016
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
helpviewer_keywords:
- CrtSetReportHook function
- _CrtSetReportHook function
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
ms.openlocfilehash: 7dcb916ea920751618ffa6a4afbcde8df5e35cba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478341"
---
# <a name="crtsetreporthook"></a>_CrtSetReportHook

Instaluje funkcję raportowania zdefiniowaną przez klienta przez podłączenie jej do procesu raportowania debugowania w czasie wykonywania C (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
_CRT_REPORT_HOOK _CrtSetReportHook(
   _CRT_REPORT_HOOK reportHook
);
```

### <a name="parameters"></a>Parametry

*reportHook*<br/>
Nowe zdefiniowaną przez klienta raportowania funkcję, aby dołączyć do środowiska wykonawczego języka C debugować proces raportowania.

## <a name="return-value"></a>Wartość zwracana

Zwraca poprzedni zdefiniowaną przez klienta funkcji raportowania.

## <a name="remarks"></a>Uwagi

**_CrtSetReportHook** pozwala aplikacji używać własnej raportowania funkcji do biblioteki debugowania w czasie wykonywania C procesu raportowania. W rezultacie, zawsze, gdy [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) nosi nazwę do wygenerowania raportu debugowania, raportowanie w aplikacji, funkcja jest wywoływana, najpierw. Ta funkcja umożliwia aplikacji wykonywanie operacji takich jak filtrowanie raportów debugowania, dzięki czemu można skupić się na określonych typów alokacji, lub wysłać raport do miejsc docelowych nie jest dostępny za pomocą **_CrtDbgReport**. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtSetReportHook** są usuwane podczas przetwarzania wstępnego.

Bardziej niezawodna wersji **_CrtSetReportHook**, zobacz [_crtsetreporthook2 —](crtsetreporthook2-crtsetreporthookw2.md).

**_CrtSetReportHook** funkcja instaluje nowy zdefiniowaną przez klienta określona w funkcji raportowania *reportHook* i zwraca poprzedniego punktu zaczepienia zdefiniowaną przez klienta. W poniższym przykładzie pokazano, jak powinny być prototypowane hook zdefiniowaną przez klienta raportu:

```C
int YourReportHook( int reportType, char *message, int *returnValue );
```

gdzie *reportType* jest typem raportu debugowania (**_CRT_WARN**, **_CRT_ERROR**, lub **_CRT_ASSERT**), *komunikat* jest zmontowanych debugowania dla użytkownika komunikat o muszą być zawarte w raporcie i **returnValue** wartość określoną przez zdefiniowaną przez klienta zgłasza funkcja, która ma zostać zwrócony przez **_ Crtdbgreport —**. Aby uzyskać pełny opis typów dostępnych raportów, zobacz [_CrtSetReportMode](crtsetreportmode.md) funkcji.

Jeśli zdefiniowaną przez klienta funkcji raportowania obsługuje całkowicie komunikat debugowania w taki sposób, że nie dalsze raportowanie jest wymagana, funkcja powinna zwrócić **TRUE**. Gdy funkcja zwraca **FALSE**, **_CrtDbgReport** jest wywoływana, aby wygenerować raport debugowania przy użyciu bieżących ustawień dla typu raportu, tryb i pliku. Ponadto, określając **_CrtDbgReport** zwracają wartości w **returnValue**, aplikację można także kontrolować, czy występuje przerwanie debugowania. Aby uzyskać pełny opis sposobu skonfigurowane i wygenerowany raport debugowania, zobacz **_CrtSetReportMode**, [_CrtSetReportFile](crtsetreportfile.md), i **_CrtDbgReport**.

Aby uzyskać więcej informacji na temat korzystania innych funkcją podłączania funkcji wykonawczej i pisanie własnych zdefiniowaną przez klienta funkcje punktów zaczepienia, zobacz [debugowania pisania funkcji punktów zaczepienia](/visualstudio/debugger/debug-hook-function-writing).

> [!NOTE]
> Jeśli aplikacja jest kompilowana z **/CLR** i funkcji raportowania jest wywoływana po zakończył działanie aplikacji głównej, środowisko CLR spowoduje zgłoszenie wyjątku, jeśli funkcja raportowania wywołuje wszystkie funkcje CRT.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtSetReportHook**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetReportHook](crtgetreporthook.md)<br/>
