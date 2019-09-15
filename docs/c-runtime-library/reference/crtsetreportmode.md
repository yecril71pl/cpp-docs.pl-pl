---
title: _CrtSetReportMode
ms.date: 11/04/2016
api_name:
- _CrtSetReportMode
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
- _CrtSetReportMode
- CrtSetReportMode
helpviewer_keywords:
- _CrtSetReportMode function
- CrtSetReportMode function
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
ms.openlocfilehash: ae7e83ac009d572f8a9f6484519b0cdfb7499ce3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938464"
---
# <a name="_crtsetreportmode"></a>_CrtSetReportMode

Określa miejsce docelowe lub docelowe dla określonego typu raportu generowanego przez **_CrtDbgReport** oraz wszystkie makra, które wywołują [_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md), takie jak [_ASSERT, _ASSERTE, _ASSERT_EXPR makra](assert-asserte-assert-expr-macros.md), [_ASSERT, _ASSERTE, _ Makra ASSERT_EXPR](assert-asserte-assert-expr-macros.md), [_RPT, _RPTF, _RPTW, _RPTFW](rpt-rptf-rptw-rptfw-macros.md)i _RPT, [_RPTF, _RPTW, _RPTFW MACROS](rpt-rptf-rptw-rptfw-macros.md) (tylko wersja Debug).

## <a name="syntax"></a>Składnia

```C
int _CrtSetReportMode(
   int reportType,
   int reportMode
);
```

### <a name="parameters"></a>Parametry

*reportType*<br/>
Typ raportu: **_CRT_WARN**, **_CRT_ERROR**i **_CRT_ASSERT**.

*raportmode*<br/>
Nowy tryb lub tryby raportu dla elementu *reportType*.

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym zakończeniu **_CrtSetReportMode** zwraca poprzedni tryb lub tryby raportu dla typu raportu określonego w elemencie *reportType*. Jeśli nieprawidłowa wartość jest przenoszona jako element *reportType* lub nieprawidłowy tryb dla elementu *ReportMode*, **_CrtSetReportMode** wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca wartość-1. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_CrtSetReportMode** określa miejsce docelowe danych wyjściowych dla **_CrtDbgReport**. Ponieważ makra [_ASSERT](assert-asserte-assert-expr-macros.md), [_ASSERTE](assert-asserte-assert-expr-macros.md), [_RPT](rpt-rptf-rptw-rptfw-macros.md)i [_RPTF](rpt-rptf-rptw-rptfw-macros.md) wywołują **_CrtDbgReport**, **_CrtSetReportMode** określa miejsce docelowe dla tekstu określonego za pomocą tych makr.

Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtSetReportMode** są usuwane podczas przetwarzania wstępnego.

Jeśli nie wywołasz **_CrtSetReportMode** w celu zdefiniowania wyjściowej lokalizacji komunikatów, obowiązują następujące wartości domyślne:

- Błędy potwierdzeń są kierowane do okna komunikatów debugowania.

- Ostrzeżenia z aplikacji systemu Windows są wysyłane do okna danych wyjściowych debugera.

- Ostrzeżenia z aplikacji konsolowych nie są wyświetlane.

Poniższa tabela zawiera listę typów raportów zdefiniowanych w pliku Crtdbg.h.

|Typ raportu|Opis|
|-----------------|-----------------|
|**_CRT_WARN**|Ostrzeżenia, komunikaty i informacje, które nie wymagają natychmiastowej uwagi.|
|**_CRT_ERROR**|Błędy, nieodwracalne problemy i kwestie, które wymagają natychmiastowej uwagi.|
|**_CRT_ASSERT**|Błędy potwierdzenia (wyrażenia potwierdzone zwracające **wartość false**).|

Funkcja **_CrtSetReportMode** przypisuje nowy tryb raportu określony w elemencie *ReportMode do typu* raportu określonego w elemencie *reportType* i zwraca poprzednio zdefiniowany tryb raportu dla elementu *reportType*. W poniższej tabeli wymieniono dostępne opcje dla elementu *ReportMode* oraz wyniki działania **_CrtDbgReport**. Te opcje są zdefiniowane jako flagi bitowe w CRTDBG. h.

|Tryb raportu|Zachowanie funkcji _CrtDbgReport|
|-----------------|-----------------------------|
|**_CRTDBG_MODE_DEBUG**|Zapisywanie komunikatu w oknie danych wyjściowych debugera.|
|**_CRTDBG_MODE_FILE**|Zapisywanie komunikatu w dojściu do pliku wskazanym przez użytkownika. [_CrtSetReportFile](crtsetreportfile.md) powinien zostać wywołany w celu zdefiniowania określonego pliku lub strumienia, który ma być używany jako miejsce docelowe.|
|**_CRTDBG_MODE_WNDW**|Tworzy okno komunikatu, aby wyświetlić komunikat wraz z przyciskami [Przerwij](abort.md), **Ponów**i **Ignoruj** .|
|**_CRTDBG_REPORT_MODE**|Zwraca wartość *ReportMode* dla określonego elementu *reportType*:<br /><br /> 1   **_CRTDBG_MODE_FILE**<br /><br /> 2   **_CRTDBG_MODE_DEBUG**<br /><br /> 4   **_CRTDBG_MODE_WNDW**|

Każdy typ raportu może być przekazywany przy użyciu jednego, dwóch lub trzech trybów albo bez żadnego trybu. Dlatego jeden typ raportu może mieć zdefiniowane więcej niż jedno miejsce docelowe. Na przykład poniższy fragment kodu powoduje wysłanie błędów potwierdzenia do okna komunikatów debugowania i do **stderr**:

```C
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );
```

Ponadto trybem lub trybami raportowania każdego typu raportu można sterować oddzielnie. Można na przykład określić, że element *reportType* elementu **_CRT_WARN** ma być wysyłany do wyjściowego ciągu debugowania, podczas gdy **_CRT_ASSERT** być wyświetlana przy użyciu okna komunikatu debugowania i wysyłanego do **stderr**, jak pokazano wcześniej.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_CrtSetReportMode**|\<crtdbg.h>|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

**Bibliotece** Debuguj tylko wersje [funkcji biblioteki CRT](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
