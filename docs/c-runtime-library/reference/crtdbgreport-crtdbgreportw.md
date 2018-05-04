---
title: _Crtdbgreport —, _crtdbgreportw — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtDbgReport
- _CrtDbgReportW
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
- CrtDbgReport
- CrtDbgReportW
- _CrtDbgReportW
- _CrtDbgReport
dev_langs:
- C++
helpviewer_keywords:
- debug reporting
- _CrtDbgReport function
- CrtDbgReport function
- CrtDbgReportW function
- _CrtDbgReportW function
ms.assetid: 6e581fb6-f7fb-4716-9432-f0145d639ecc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57290d2985036ea3df2863e175d742c819a3fe03
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="crtdbgreport-crtdbgreportw"></a>_CrtDbgReport, _CrtDbgReportW

Generuje raport z komunikatem debugowania i wysyła raport do trzech miejsc docelowych możliwe (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
int _CrtDbgReport(
   int reportType,
   const char *filename,
   int linenumber,
   const char *moduleName,
   const char *format [,
   argument] ...
);
int _CrtDbgReportW(
   int reportType,
   const wchar_t *filename,
   int linenumber,
   const wchar_t *moduleName,
   const wchar_t *format [,
   argument] ...
);
```

### <a name="parameters"></a>Parametry

*reportType*<br/>
Typ raportu: **_CRT_WARN**, **_CRT_ERROR**, i **_CRT_ASSERT**.

*Nazwa pliku*<br/>
Wskaźnik do nazwy pliku źródłowego, w którym wystąpił assert raportu lub **NULL**.

*numer wiersza*<br/>
Numer wiersza na plik źródłowy, na którym wystąpił assert raportu lub **NULL**.

*Nazwa modułu*<br/>
Wskaźnik do nazwy modułu (.exe lub .dll) gdzie assert lub wystąpił raportu.

*Format*<br/>
Wskaźnik do sterowania format ciąg używany do tworzenia komunikat.

*Argument*<br/>
Argumenty opcjonalne podstawienia używane przez *format*.

## <a name="return-value"></a>Wartość zwracana

Dla wszystkich raportów miejsc docelowych **_crtdbgreport —** i **_crtdbgreportw —** Zwróć -1, jeśli wystąpi błąd i 0, jeśli nie zostaną napotkane żadne błędy. Jednak gdy raport docelowy jest użytkownika i debugowania okna komunikatu kliknie **ponów** przycisku Funkcje zwracają 1. Gdy użytkownik kliknie **przerwać** przycisk w oknie komunikatu debugowania tych funkcji natychmiast przerwania i nie zwraca wartości.

[_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) debugowania wywołanie makra **_crtdbgreport —** do ich debugowania generowania raportów. Wersje znaków dwubajtowych tych makr oraz [_ASSERT, _asserte —](assert-asserte-assert-expr-macros.md), [_RPTW](rpt-rptf-rptw-rptfw-macros.md) i [_rptfw —](rpt-rptf-rptw-rptfw-macros.md), użyj **_crtdbgreportw —** do Generowanie raportów ich debugowania. Gdy **_crtdbgreport —** lub **_crtdbgreportw —** zwraca 1, te makra uruchomienia debugera, pod warunkiem, że włączone jest debugowanie just-in-time (JIT).

## <a name="remarks"></a>Uwagi

**_Crtdbgreport —** i **_crtdbgreportw —** wysłać raport debugowania do trzech różnych miejsc docelowych: plik raportu debugowania, monitor debugowania (debuger programu Visual Studio) lub oknie wiadomości debugowania. Dwie funkcje konfiguracji, [_crtsetreportmode —](crtsetreportmode.md) i [_crtsetreportfile —](crtsetreportfile.md), są używane do określenia przeznaczenia lub miejsc docelowych dla każdego typu raportu. Te funkcje umożliwiają raportowania docelowego lub miejsc docelowych dla każdego typu raportu można sterować oddzielnie. Na przykład użytkownik może określić, że *reportType* z **_CRT_WARN** tylko być wysyłane do monitora debugowania, podczas gdy *reportType* z **_CRT_ASSERT** wysłane do pliku raportu zdefiniowane przez użytkownika i debugowania okna komunikatu.

**_Crtdbgreportw —** jest wersja znaków dwubajtowych **_crtdbgreport —**. Wszystkie jej dane wyjściowe i ciąg parametry są w ciągach znaków dwubajtowych; w przeciwnym razie jest taka sama jak wersja znaków.

**_Crtdbgreport —** i **_crtdbgreportw —** utworzyć komunikat raportu debugowania podstawiając *argument*[**n**] argumenty do *format* ciąg znaków, według reguł zdefiniowanych przez **printf** lub **wprintf** funkcji. Te funkcje następnie wygeneruj raport debugowania i określenia przeznaczenia lub miejsc docelowych, które są oparte na trybie Bieżące raportu i pliku zdefiniowane dla *reportType*. Gdy raport jest wysyłany do okna komunikatu debugowania, *filename*, **numer wiersza**, i *moduleName* znajdują się informacje wyświetlane w oknie.

W poniższej tabeli wymieniono dostępne opcje dla trybie raportu lub trybów plików i zachowanie wynikowy **_crtdbgreport —** i **_crtdbgreportw —**. Te opcje są zdefiniowane jako flagi bitów w \<crtdbg.h >.

|Tryb raportu|Plik raportu|**_Crtdbgreport —**, **_crtdbgreportw —** zachowanie|
|-----------------|-----------------|------------------------------------------------|
|**_CRTDBG_MODE_DEBUG**|Nie dotyczy|Zapisuje komunikat przy użyciu systemu Windows [OutputDebugString](http://msdn.microsoft.com/library/windows/desktop/aa363362.aspx) interfejsu API.|
|**_CRTDBG_MODE_WNDW**|Nie dotyczy|Wymaga systemu Windows [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) interfejsu API, aby utworzyć komunikat do wyświetlenia komunikatu, wraz z **przerwać**, **ponów**, i **Ignoruj** przycisków. Gdy użytkownik kliknie **przerwać**, **_crtdbgreport —** lub **_crtdbgreport —** natychmiastowe przerwanie. Gdy użytkownik kliknie **ponów**, zwraca 1. Gdy użytkownik kliknie **Ignoruj**, wykonanie jest kontynuowane i **_crtdbgreport —** i **_crtdbgreportw —** zwraca 0. Należy pamiętać, że kliknięcie pozycji **Ignoruj** gdy warunek błędu istnieje często skutkuje "niezdefiniowane zachowanie."|
|**_CRTDBG_MODE_FILE**|**__HFILE**|Zapisuje komunikat do podanego użytkownika **obsługi**, przy użyciu systemu Windows [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747.aspx) interfejsu API i nie sprawdza poprawność dojście do pliku; aplikacji jest odpowiedzialny za otwieranie pliku raportu i przekazywanie pliku dojście.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDERR**|Zapisuje komunikat do **stderr**.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDOUT**|Zapisuje komunikat do **stdout**.|

Raport mogą być wysyłane do jednego, dwóch lub trzech miejsc docelowych lub nie docelowego w ogóle. Aby uzyskać więcej informacji na temat określania trybu raportu lub tryby i plik raportu, zobacz [_crtsetreportmode —](crtsetreportmode.md) i [_crtsetreportfile —](crtsetreportfile.md) funkcji. Aby uzyskać więcej informacji o użyciu makra debugowania i funkcje raportowania, zobacz [makra dla raportowania](/visualstudio/debugger/macros-for-reporting).

Jeśli aplikacja wymaga większą elastyczność niż te dostarczone przez **_crtdbgreport —** i **_crtdbgreportw —**, możesz zapisać własnego raportowania funkcji i utworzenie punktu zaczepienia w raporcie biblioteki wykonawczej języka C mechanizm, za pomocą [_crtsetreporthook —](crtsetreporthook.md) funkcji.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtDbgReport**|\<crtdbg.h>|
|**_CrtDbgReportW**|\<crtdbg.h>|

**_Crtdbgreport —** i **_crtdbgreportw —** są rozszerzenia Microsoft. Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

```C
// crt_crtdbgreport.c
#include <crtdbg.h>

int main(int argc, char *argv[]) {
#ifdef _DEBUG
   _CrtDbgReport(_CRT_ASSERT, __FILE__, __LINE__, argv[0], NULL);
#endif
}
```

Zobacz [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2) przykład sposobu zmiany funkcji raportu.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportMode](crtsetreportmode.md)<br/>
[_CrtSetReportFile](crtsetreportfile.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
