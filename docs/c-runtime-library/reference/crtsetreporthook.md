---
title: _CrtSetReportHook
ms.date: 11/04/2016
api_name:
- _CrtSetReportHook
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CrtSetReportHook
- CrtSetReportHook
helpviewer_keywords:
- CrtSetReportHook function
- _CrtSetReportHook function
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
ms.openlocfilehash: 77c1e499c66a76027e872783e256754ef72e465d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938513"
---
# <a name="_crtsetreporthook"></a>_CrtSetReportHook

Instaluje funkcję raportowania zdefiniowaną przez klienta, przełączając ją do procesu raportowania debugowania w czasie wykonywania C (tylko wersja Debug).

## <a name="syntax"></a>Składnia

```C
_CRT_REPORT_HOOK _CrtSetReportHook(
   _CRT_REPORT_HOOK reportHook
);
```

### <a name="parameters"></a>Parametry

*reportHook*<br/>
Nowa funkcja raportowania zdefiniowana przez klienta do podłączania do procesu raportowania debugowania w czasie wykonywania języka C.

## <a name="return-value"></a>Wartość zwracana

Zwraca poprzednią funkcję raportowania zdefiniowaną przez klienta.

## <a name="remarks"></a>Uwagi

**_CrtSetReportHook** umożliwia aplikacji użycie własnej funkcji raportowania w procesie raportowania biblioteki debugowania w czasie wykonywania C. W związku z tym zawsze, gdy [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) jest wywoływana w celu wygenerowania raportu debugowania, funkcja raportowania aplikacji jest wywoływana jako pierwsza. Ta funkcja umożliwia aplikacji wykonywanie operacji, takich jak filtrowanie raportów debugowania, aby można było skupić się na określonych typach alokacji lub wysłać raport do miejsc docelowych, które nie są dostępne za pomocą **_CrtDbgReport**. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtSetReportHook** są usuwane podczas przetwarzania wstępnego.

Aby uzyskać bardziej niezawodną wersję programu **_CrtSetReportHook**, zobacz [_CrtSetReportHook2](crtsetreporthook2-crtsetreporthookw2.md).

Funkcja **_CrtSetReportHook** instaluje nową funkcję raportowania zdefiniowaną przez klienta określoną w *reportHook* i zwraca poprzedni zdefiniowany przez klienta punkt zaczepienia. W poniższym przykładzie pokazano, jak ma być prototypem punkt zaczepienia raportu zdefiniowanego przez klienta:

```C
int YourReportHook( int reportType, char *message, int *returnValue );
```

Jeśli *reportType* jest typem raportu debugowania ( **_CRT_WARN**, **_CRT_ERROR**lub **_CRT_ASSERT**), *komunikat* jest w pełni zmontowany komunikat użytkownika debugowania, który zostanie zawarty w raporcie, a **ReturnValue** jest wartością określony przez zdefiniowaną przez klienta funkcję raportowania, która powinna zostać zwrócona przez **_CrtDbgReport**. Pełny opis dostępnych typów raportów można znaleźć w funkcji [_CrtSetReportMode](crtsetreportmode.md) .

Jeśli funkcja raportowania zdefiniowane przez klienta całkowicie obsługuje komunikat debugowania, taki jak nie jest wymagane dalsze raportowanie, funkcja powinna zwrócić **wartość true**. Gdy funkcja zwraca **wartość false**, **_CrtDbgReport** jest wywoływana w celu wygenerowania raportu debugowania przy użyciu bieżących ustawień typu raportu, trybu i pliku. Ponadto przez określenie wartości zwracanej **_CrtDbgReport** w **ReturnValue**, aplikacja może również kontrolować, czy występuje przerwanie debugowania. Pełny opis sposobu konfiguracji i generowania raportu debugowania można znaleźć w tematach **_CrtSetReportMode**, [_CrtSetReportFile](crtsetreportfile.md)i **_CrtDbgReport**.

Aby uzyskać więcej informacji na temat korzystania z innych funkcji w czasie wykonywania z możliwością podłączania i pisania własnych zdefiniowanych przez klienta funkcji Hook, zobacz [Zapisywanie funkcji punktu zaczepienia debugowania](/visualstudio/debugger/debug-hook-function-writing).

> [!NOTE]
> Jeśli aplikacja jest skompilowana z **/CLR** , a funkcja raportowania jest wywoływana po zakończeniu głównego poziomu aplikacji, środowisko CLR zgłosi wyjątek, jeśli funkcja raportowania wywoła wszystkie funkcje CRT.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtSetReportHook**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje wyłącznie [bibliotek uruchomieniowych C](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetReportHook](crtgetreporthook.md)<br/>
