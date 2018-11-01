---
title: _CrtSetReportMode
ms.date: 11/04/2016
apiname:
- _CrtSetReportMode
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
- _CrtSetReportMode
- CrtSetReportMode
helpviewer_keywords:
- _CrtSetReportMode function
- CrtSetReportMode function
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
ms.openlocfilehash: 2096d39a8ba316fc76c97517a16e34231940e7f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595536"
---
# <a name="crtsetreportmode"></a>_CrtSetReportMode

Określa miejsce lub miejsca docelowe dla określonego typu raportu generowanego przez **_CrtDbgReport** oraz dla wszelkich makra, które wywołują [_CrtDbgReport, _crtdbgreportw —](crtdbgreport-crtdbgreportw.md), takich jak [_ASSERT, _asserte —, Makra _ASSERT_EXPR](assert-asserte-assert-expr-macros.md), [_ASSERT, _asserte —, makra _ASSERT_EXPR](assert-asserte-assert-expr-macros.md), [_RPT, _RPTF, _RPTW, _rptfw — makra](rpt-rptf-rptw-rptfw-macros.md), i [_RPT, _RPTF, _RPTW, _rptfw — makra](rpt-rptf-rptw-rptfw-macros.md) (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
int _CrtSetReportMode(
   int reportType,
   int reportMode
);
```

### <a name="parameters"></a>Parametry

*reportType*<br/>
Typ raportu: **_CRT_WARN**, **_CRT_ERROR**, i **_CRT_ASSERT**.

*ReportMode.*<br/>
Nowy tryb lub tryby raportu dla *reportType*.

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym zakończeniu **_CrtSetReportMode** zwraca poprzedniego tryb lub tryby raportu dla typu raportu określonego *reportType*. Jeśli nieprawidłowa wartość jest przekazywana jako *reportType* lub określono nieprawidłowy tryb *ReportMode*, **_CrtSetReportMode** wywołuje program obsługi nieprawidłowych parametrów jako opisane w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca wartość -1. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_CrtSetReportMode** określa miejsce docelowe danych wyjściowych dla **_CrtDbgReport**. Ponieważ makra [_ASSERT](assert-asserte-assert-expr-macros.md), [_asserte —](assert-asserte-assert-expr-macros.md), [_RPT](rpt-rptf-rptw-rptfw-macros.md), i [_RPTF](rpt-rptf-rptw-rptfw-macros.md) wywołania **_CrtDbgReport**, **_CrtSetReportMode** Określa lokalizację wyjściową tekstu objętego makrami.

Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtSetReportMode** są usuwane podczas przetwarzania wstępnego.

Jeśli nie zostanie wywołana **_CrtSetReportMode** do zdefiniowania lokalizacji wyjściowej komunikatów, następnie następujące wartości domyślne są stosowane:

- Błędy potwierdzeń są kierowane do okna komunikatów debugowania.

- Ostrzeżenia z aplikacji systemu Windows są wysyłane do okna danych wyjściowych debugera.

- Ostrzeżenia z aplikacji konsolowych nie są wyświetlane.

Poniższa tabela zawiera listę typów raportów zdefiniowanych w pliku Crtdbg.h.

|Typ raportu|Opis|
|-----------------|-----------------|
|**_CRT_WARN**|Ostrzeżenia, komunikaty i informacje, które nie wymagają natychmiastowej uwagi.|
|**_CRT_ERROR**|Błędy, nieodwracalne problemy i kwestie, które wymagają natychmiastowej uwagi.|
|**_CRT_ASSERT**|Błędy potwierdzeń (potwierdzanego wyrażeniami, które obliczają do **FALSE**).|

**_CrtSetReportMode** funkcja przypisuje nowy tryb raportu określony w *ReportMode* do typu raportu określonego w *reportType* i zwraca uprzednio zdefiniowany Tryb raportu *reportType*. W poniższej tabeli przedstawiono dostępne opcje *ReportMode* i zachowanie wynikową **_CrtDbgReport**. Te opcje są zdefiniowane jako flaga bitowych w Crtdbg.h.

|Tryb raportu|Zachowanie funkcji _CrtDbgReport|
|-----------------|-----------------------------|
|**_CRTDBG_MODE_DEBUG**|Zapisywanie komunikatu w oknie danych wyjściowych debugera.|
|**_CRTDBG_MODE_FILE**|Zapisywanie komunikatu w dojściu do pliku wskazanym przez użytkownika. [_CrtSetReportFile](crtsetreportfile.md) powinna być wywoływana w celu definiowania określonego pliku lub strumienia mającego służyć jako miejsce docelowe.|
|**_CRTDBG_MODE_WNDW**|Tworzy okno komunikatu, aby wyświetlić wiadomość wraz z [przerwać](abort.md), **ponów**, i **Ignoruj** przycisków.|
|**_CRTDBG_REPORT_MODE**|Zwraca *ReportMode* dla określonego *reportType*:<br /><br /> 1 **_CRTDBG_MODE_FILE**<br /><br /> 2 **_CRTDBG_MODE_DEBUG**<br /><br /> 4 **_CRTDBG_MODE_WNDW**|

Każdy typ raportu może być przekazywany przy użyciu jednego, dwóch lub trzech trybów albo bez żadnego trybu. Dlatego jeden typ raportu może mieć zdefiniowane więcej niż jedno miejsce docelowe. Na przykład poniższy fragment kodu powoduje błędy potwierdzenia do wysłania do oba okna komunikatów debugowania i do **stderr**:

```C
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );
```

Ponadto trybem lub trybami raportowania każdego typu raportu można sterować oddzielnie. Na przykład, istnieje możliwość określić, że *reportType* z **_CRT_WARN** być wysyłane do ciągu debugowania danych wyjściowych, podczas gdy **_CRT_ASSERT** być wyświetlana przy użyciu okna komunikatów debugowania i wysyłane do **stderr**, jak przedstawiono wcześniej.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_CrtSetReportMode**|\<crtdbg.h>|\<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

**Biblioteki:** Debuguj wersje [funkcje biblioteki CRT](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
