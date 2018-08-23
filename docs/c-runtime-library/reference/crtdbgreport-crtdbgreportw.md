---
title: _CrtDbgReport, _crtdbgreportw — | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: b2b0bcdc5ee6c4c2b71837f1cdd958f50d8d0b4a
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2018
ms.locfileid: "42465903"
---
# <a name="crtdbgreport-crtdbgreportw"></a>_CrtDbgReport, _CrtDbgReportW

Generuje raport z komunikatem debugowania i wysyła raport do trzech możliwych miejsc docelowych (tylko wersja debugowania).

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
Wskaźnik na nazwę pliku źródłowego, w którym wystąpił wystąpiło zapewnienie/raport lub **NULL**.

*numer wiersza*<br/>
Numer wiersza w pliku źródłowym, gdzie wystąpiło wystąpiło zapewnienie/raport lub **NULL**.

*Nazwa modułu*<br/>
Wskaźnik na nazwę modułu (.exe lub .dll) gdzie wystąpiło zapewnienie lub raport.

*Format*<br/>
Wskaźnik na sterowania formatem ciągu używany do tworzenia wiadomości użytkownika.

*Argument*<br/>
Argumenty opcjonalne podstawiania używane przez *format*.

## <a name="return-value"></a>Wartość zwracana

Dla wszystkich miejsc docelowych raportów **_CrtDbgReport** i **_crtdbgreportw —** zwraca -1, jeśli wystąpi błąd i 0, jeśli zostaną napotkane żadne błędy. Jednakże, gdy miejscem docelowym raportu jest okno komunikatu debugowania i użytkownik klika **ponów** przycisku, funkcje te zwracają 1. Jeśli użytkownik kliknie **przerwać** przycisku w oknie komunikatów debugowania, funkcje te natychmiast przerwać i nie zwraca wartości.

[_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) Debuguj wywołania makr **_CrtDbgReport** do generowania ich debugowania raportów. Wersjami szerokich znaków tych makr oraz [_ASSERT, _asserte —](assert-asserte-assert-expr-macros.md), [_RPTW](rpt-rptf-rptw-rptfw-macros.md) i [_rptfw —](rpt-rptf-rptw-rptfw-macros.md), użyj **_crtdbgreportw —** do generować ich raporty debugowania. Gdy **_CrtDbgReport** lub **_crtdbgreportw —** zwraca 1, te makra uruchamiają debugera, pod warunkiem, że włączone jest debugowanie just-in-time (JIT).

## <a name="remarks"></a>Uwagi

**_CrtDbgReport** i **_crtdbgreportw —** wysłać raport debugowania do trzech różnych miejsc docelowych: pliku raportu debugowania, monitora debugowania (debugera programu Visual Studio) lub okna komunikatów debugowania. Dwie funkcje konfiguracji [_CrtSetReportMode](crtsetreportmode.md) i [_CrtSetReportFile](crtsetreportfile.md), są używane do określania miejsca przeznaczenia lub miejsca docelowe dla każdego typu raportu. Funkcje te zezwalają na raportowania miejsca przeznaczenia lub miejsca docelowe dla każdego typu raportu można sterować oddzielnie. Na przykład, istnieje możliwość określić, że *reportType* z **_CRT_WARN** składać się wyłącznie wysłanych do monitora debugowania, podczas gdy *reportType* z **_CRT_ASSERT** wysyłane do okna komunikatów debugowania i plik raportu zdefiniowany przez użytkownika.

**_Crtdbgreportw —** jest wersją znaków dwubajtowych **_CrtDbgReport**. Wszystkie jego dane wyjściowe i parametry ciągu są w ciągach znaków dwubajtowych; w przeciwnym razie jest identyczna z wersją znaków jednobajtowych.

**_CrtDbgReport** i **_crtdbgreportw —** tworzą wiadomość użytkownika do raportu debugowania zastępując *argument*[**n**] argumenty do *format* ciąg znaków, przy użyciu tych samych zasad zdefiniowanych przez **printf** lub **wprintf** funkcji. Funkcje te następnie generują raport debugowania i określają miejsca przeznaczenia lub miejsca, w oparciu o bieżące tryby raportów i plik zdefiniowany dla *reportType*. Gdy raport jest wysyłany do okna komunikatów debugowania, *filename*, **lineNumber**, i *moduleName* znajdują się w informacjach wyświetlanych w oknie.

W poniższej tabeli przedstawiono dostępne opcje trybu raportu lub trybów i plików i wynikowe zachowania funkcji **_CrtDbgReport** i **_crtdbgreportw —**. Te opcje są zdefiniowane jako flaga bitowych w \<crtdbg.h >.

|Tryb raportu|Plik raportu|**_CrtDbgReport**, **_crtdbgreportw —** zachowanie|
|-----------------|-----------------|------------------------------------------------|
|**_CRTDBG_MODE_DEBUG**|Nie dotyczy|Zapisuje komunikat przy użyciu Windows [OutputDebugString](http://msdn.microsoft.com/library/windows/desktop/aa363362.aspx) interfejsu API.|
|**_CRTDBG_MODE_WNDW**|Nie dotyczy|Wywołuje Windows [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) interfejsu API w celu tworzenia okna komunikatu, aby wyświetlić wiadomość wraz z **przerwać**, **ponów**, i **Ignoruj** przycisków. Jeśli użytkownik kliknie **przerwać**, **_CrtDbgReport** lub **_CrtDbgReport** niezwłocznie przerywa. Jeśli użytkownik kliknie **ponów**, zwraca wartość 1. Jeśli użytkownik kliknie **Ignoruj**, wykonywanie jest kontynuowane i **_CrtDbgReport** i **_crtdbgreportw —** zwracają 0. Należy pamiętać, że kliknięcie **Ignoruj** kiedy warunek błędu istnieje często powoduje "nieokreślone zachowanie".|
|**_CRTDBG_MODE_FILE**|**__HFILE**|Wpisuje wiadomość do dostarczone przez użytkownika **obsługi**, przy użyciu Windows [WriteFile](/windows/desktop/api/fileapi/nf-fileapi-writefile) API i nie sprawdza poprawności dojścia do pliku; aplikacja jest odpowiedzialna za otwarcie pliku raportu i przekazywanie pliku dojście.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDERR**|Wpisuje wiadomość do **stderr**.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDOUT**|Wpisuje wiadomość do **stdout**.|

Raport może być wysyłany do jednego, dwóch lub trzech miejsc docelowych lub nie miejsca docelowego w ogóle. Aby uzyskać więcej informacji na temat określania trybu raportu lub trybów i plików raportu, zobacz [_CrtSetReportMode](crtsetreportmode.md) i [_CrtSetReportFile](crtsetreportfile.md) funkcji. Aby uzyskać więcej informacji na temat korzystania z makr debugowania i funkcji raportowania, zobacz [makra dla raportowania](/visualstudio/debugger/macros-for-reporting).

Jeśli aplikacja wymaga większej elastyczności niż ta dostarczona przez **_CrtDbgReport** i **_crtdbgreportw —**, można napisać własną funkcję raportowania i podłączyć ją do raportowania biblioteki wykonawczej języka C mechanizm, za pomocą [_CrtSetReportHook](crtsetreporthook.md) funkcji.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtDbgReport**|\<crtdbg.h>|
|**_CrtDbgReportW**|\<crtdbg.h>|

**_CrtDbgReport** i **_crtdbgreportw —** są rozszerzeniami Microsoft. Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

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

Zobacz [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2) przykład sposób zmiany funkcji raportu.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportMode](crtsetreportmode.md)<br/>
[_CrtSetReportFile](crtsetreportfile.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
