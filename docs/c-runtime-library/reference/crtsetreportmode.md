---
title: _Crtsetreportmode — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _CrtSetReportMode function
- CrtSetReportMode function
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd4ac54cd4bd8877e8a6ba32f585ef5d5e29e65c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403264"
---
# <a name="crtsetreportmode"></a>_CrtSetReportMode

Określa docelowy lub miejsc docelowych dla typu określonego raportu generowane przez **_crtdbgreport —** i makr, które wywołują [_crtdbgreport —, _crtdbgreportw —](crtdbgreport-crtdbgreportw.md), takich jak [_ASSERT, _asserte —, Makra _ASSERT_EXPR](assert-asserte-assert-expr-macros.md), [_ASSERT, _asserte —, makra _ASSERT_EXPR](assert-asserte-assert-expr-macros.md), [_RPT, _RPTF, _RPTW, _rptfw — makra](rpt-rptf-rptw-rptfw-macros.md), i [_RPT, _RPTF, _RPTW, _rptfw — makra](rpt-rptf-rptw-rptfw-macros.md) (tylko wersja debugowania).

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
Nowy tryb raportu lub tryby *reportType*.

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym ukończeniu **_crtsetreportmode —** zwraca tryb poprzedniego raportu lub tryby dla określonego typu raportu w *reportType*. Jeśli wartość jest nieprawidłowa jest przekazywany jako *reportType* lub określono nieprawidłowy tryb *ReportMode*, **_crtsetreportmode —** wywołuje program obsługi nieprawidłowych parametrów jako opisany w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia **errno** do **einval —** i zwraca wartość -1. Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Crtsetreportmode —** określa miejsce docelowe danych wyjściowych dla **_crtdbgreport —**. Ponieważ makra [_ASSERT](assert-asserte-assert-expr-macros.md), [_asserte —](assert-asserte-assert-expr-macros.md), [_RPT](rpt-rptf-rptw-rptfw-macros.md), i [_RPTF](rpt-rptf-rptw-rptfw-macros.md) wywołać **_crtdbgreport —**, **_Crtsetreportmode —** określa miejsce docelowe danych wyjściowych tekstu określonego przy użyciu tych makr.

Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań **_crtsetreportmode —** są usuwane podczas przetwarzania wstępnego.

Jeśli nie zostanie wywołana **_crtsetreportmode —** Aby zdefiniować miejsce docelowe danych wyjściowych wiadomości, następnie następujące parametry domyślne działają:

- Błędy potwierdzeń są kierowane do okna komunikatów debugowania.

- Ostrzeżenia z aplikacji systemu Windows są wysyłane do okna danych wyjściowych debugera.

- Ostrzeżenia z aplikacji konsolowych nie są wyświetlane.

Poniższa tabela zawiera listę typów raportów zdefiniowanych w pliku Crtdbg.h.

|Typ raportu|Opis|
|-----------------|-----------------|
|**_CRT_WARN**|Ostrzeżenia, komunikaty i informacje, które nie wymagają natychmiastowej uwagi.|
|**_CRT_ERROR**|Błędy, nieodwracalne problemy i kwestie, które wymagają natychmiastowej uwagi.|
|**_CRT_ASSERT**|Błędy potwierdzenia (potwierdzone wyrażeń określających **FALSE**).|

**_Crtsetreportmode —** funkcja przypisuje nowy tryb raportu określone w *ReportMode* typ raportu, określony w *reportType* i zwraca uprzednio zdefiniowany Tryb raportu *reportType*. W poniższej tabeli wymieniono dostępne opcje dla *ReportMode* i wynikowy zachowania **_crtdbgreport —**. Te opcje są definiowane jako flagi bitów w Crtdbg.h.

|Tryb raportu|Zachowanie funkcji _CrtDbgReport|
|-----------------|-----------------------------|
|**_CRTDBG_MODE_DEBUG**|Zapisywanie komunikatu w oknie danych wyjściowych debugera.|
|**_CRTDBG_MODE_FILE**|Zapisywanie komunikatu w dojściu do pliku wskazanym przez użytkownika. [_Crtsetreportfile —](crtsetreportfile.md) powinna być wywoływana w celu zdefiniowania określonego pliku lub strumienia ma być używana jako miejsce docelowe.|
|**_CRTDBG_MODE_WNDW**|Tworzy okno komunikatu do wyświetlania komunikatu o wraz z [przerwać](abort.md), **ponów**, i **Ignoruj** przycisków.|
|**_CRTDBG_REPORT_MODE**|Zwraca *ReportMode* dla określonego *reportType*:<br /><br /> 1 **_CRTDBG_MODE_FILE**<br /><br /> 2 **_CRTDBG_MODE_DEBUG**<br /><br /> 4 **_CRTDBG_MODE_WNDW**|

Każdy typ raportu może być przekazywany przy użyciu jednego, dwóch lub trzech trybów albo bez żadnego trybu. Dlatego jeden typ raportu może mieć zdefiniowane więcej niż jedno miejsce docelowe. Na przykład poniższy fragment kodu powoduje błędy potwierdzenia do wysłania do obu okno komunikatu debugowania oraz na **stderr**:

```C
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );
```

Ponadto trybem lub trybami raportowania każdego typu raportu można sterować oddzielnie. Na przykład użytkownik może określić, że *reportType* z **_CRT_WARN** być przesyłany do ciągu wyjściowego debugowania, podczas gdy **_CRT_ASSERT** można wyświetlane przy użyciu okna komunikatu debugowania i wysyłane do **stderr**, wcześniej ilustrowane.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_CrtSetReportMode**|\<crtdbg.h>|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

**Biblioteki:** wersja debugowania [Biblioteka CRT — funkcje](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
