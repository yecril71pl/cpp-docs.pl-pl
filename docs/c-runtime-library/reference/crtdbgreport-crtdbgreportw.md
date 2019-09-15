---
title: _CrtDbgReport, _CrtDbgReportW
ms.date: 11/04/2016
api_name:
- _CrtDbgReport
- _CrtDbgReportW
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
- CrtDbgReport
- CrtDbgReportW
- _CrtDbgReportW
- _CrtDbgReport
helpviewer_keywords:
- debug reporting
- _CrtDbgReport function
- CrtDbgReport function
- CrtDbgReportW function
- _CrtDbgReportW function
ms.assetid: 6e581fb6-f7fb-4716-9432-f0145d639ecc
ms.openlocfilehash: 986777f755a749e858f7e51b5aa19f10090db13a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938839"
---
# <a name="_crtdbgreport-_crtdbgreportw"></a>_CrtDbgReport, _CrtDbgReportW

Generuje raport z komunikatem debugowania i wysyła raport do trzech możliwych miejsc docelowych (tylko wersja do debugowania).

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
Typ raportu: **_CRT_WARN**, **_CRT_ERROR**i **_CRT_ASSERT**.

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, w którym wystąpiło potwierdzenie/raport lub **wartość null**.

*LineNumber*<br/>
Numer wiersza w pliku źródłowym, w którym wystąpiło potwierdzenie/raport lub **wartość null**.

*moduleName*<br/>
Wskaźnik na nazwę modułu (. exe lub. dll), w którym wystąpiło potwierdzenie lub raport.

*format*<br/>
Wskaźnik do formatu — ciąg kontrolny użyty do utworzenia komunikatu użytkownika.

*argument*<br/>
Opcjonalne argumenty podstawienia używane przez *Format*.

## <a name="return-value"></a>Wartość zwracana

Dla wszystkich miejsc docelowych raportów, **_CrtDbgReport** i **_CrtDbgReportW** Zwróć-1, jeśli wystąpi błąd i 0, jeśli nie zostaną napotkane żadne błędy. Jeśli jednak miejsce docelowe raportu jest oknem komunikatu debugowania, a użytkownik kliknie przycisk **Ponów próbę** , te funkcje zwracają wartość 1. Jeśli użytkownik kliknie przycisk **Przerwij** w oknie komunikatu debugowania, te funkcje natychmiast Przerwij i nie zwracają wartości.

Makra debugowania [_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) wywołania **_CrtDbgReport** w celu wygenerowania ich raportów debugowania. Wersje o szerokim znaku tych makr, a także [_ASSERT, _ASSERTE](assert-asserte-assert-expr-macros.md), [_RPTW](rpt-rptf-rptw-rptfw-macros.md) i [_RPTFW](rpt-rptf-rptw-rptfw-macros.md), używają **_CrtDbgReportW** do generowania raportów debugowania. Gdy **_CrtDbgReport** lub **_CrtDbgReportW** zwracają 1, te makra uruchamiają debuger, pod warunkiem że włączone jest debugowanie just-in-Time (JIT).

## <a name="remarks"></a>Uwagi

**_CrtDbgReport** i **_CrtDbgReportW** mogą wysyłać raport debugowania do trzech różnych miejsc docelowych: plik raportu debugowania, Monitor debugowania (debuger programu Visual Studio) lub okno komunikatu debugowania. Dwie funkcje konfiguracji, [_CrtSetReportMode](crtsetreportmode.md) i [_CrtSetReportFile](crtsetreportfile.md), służą do określania miejsca docelowego i miejsc docelowych dla każdego typu raportu. Te funkcje umożliwiają niezależne sterowanie miejscem docelowym raportowania lub miejsc docelowych dla każdego typu raportu. Można na przykład określić, że element *reportType* elementu **_CRT_WARN** ma być wysyłany tylko do monitora debugowania, podczas gdy *raport* typu **_CRT_ASSERT** jest wysyłany do okna komunikatu debugowania i pliku raportu zdefiniowanego przez użytkownika.

**_CrtDbgReportW** to dwubajtowa wersja **_CrtDbgReport**. Wszystkie parametry danych wyjściowych i ciągów są ciągami znaków dwubajtowych; w przeciwnym razie jest taka sama jak wersja znaku jednobajtowego.

**_CrtDbgReport** i **_CrtDbgReportW** Utwórz komunikat użytkownika dla raportu debugowania, zastępując argumenty *argumentu*[**n**] do ciągu *formatu* , używając tych samych reguł zdefiniowanych przez **printf** lub  **funkcje wprintf** . Te funkcje następnie generują raport debugowania i określają miejsce docelowe lub docelowe w oparciu o bieżące tryby raportu i plik zdefiniowany dla elementu *reportType*. Gdy raport jest wysyłany do okna komunikatu debugowania, *nazwy pliku*, **LineNumber**i *ModuleName* są zawarte w informacjach wyświetlanych w oknie.

Poniższa tabela zawiera listę dostępnych opcji trybu lub trybów raportów oraz pliku oraz zachowanie wyników **_CrtDbgReport** i **_CrtDbgReportW**. Te opcje są zdefiniowane jako flagi bitowe w \<CRTDBG. h >.

|Tryb raportu|Plik raportu|**_CrtDbgReport**, zachowanie **_CrtDbgReportW**|
|-----------------|-----------------|------------------------------------------------|
|**_CRTDBG_MODE_DEBUG**|Nie dotyczy|Zapisuje komunikat przy użyciu interfejsu API [Funkcja OutputDebugString](/windows/win32/api/debugapi/nf-debugapi-outputdebugstringw) systemu Windows.|
|**_CRTDBG_MODE_WNDW**|Nie dotyczy|Wywołuje interfejs API [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) systemu Windows w celu utworzenia okna komunikatu, aby wyświetlić komunikat wraz z przyciskami **przerywania**, **ponawiania**i **ignorowania** . Jeśli użytkownik kliknie przycisk **Przerwij**, **_CrtDbgReport** lub **_CrtDbgReport** natychmiast przerywa. Jeśli użytkownik kliknie przycisk **Ponów próbę**, zwraca wartość 1. Jeśli użytkownik kliknie przycisk **Ignoruj**, wykonywanie jest kontynuowane, a **_CrtDbgReport** i **_CrtDbgReportW** zwracają 0. Należy pamiętać, że kliknięcie przycisku **Ignoruj** , gdy istnieje warunek błędu często powoduje "niezdefiniowane zachowanie".|
|**_CRTDBG_MODE_FILE**|**__HFILE**|Zapisuje komunikat do **dojścia**dostarczonego przez użytkownika przy użyciu interfejsu API [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile) systemu Windows i nie weryfikuje ważności dojścia do pliku; Aplikacja jest odpowiedzialna za otwarcie pliku raportu i przekazanie prawidłowego dojścia do pliku.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDERR**|Zapisuje komunikat do **stderr**.|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDOUT**|Zapisuje komunikat w strumieniu **stdout**.|

Raport może być wysyłany do jednego, dwóch lub trzech miejsc docelowych lub nie do miejsca docelowego. Aby uzyskać więcej informacji na temat określania trybu raportu lub trybów i pliku raportu, zobacz funkcje [_CrtSetReportMode](crtsetreportmode.md) i [_CrtSetReportFile](crtsetreportfile.md) . Aby uzyskać więcej informacji na temat korzystania z makr debugowania i funkcji raportowania, zobacz [MACROS for Reporting](/visualstudio/debugger/macros-for-reporting).

Jeśli aplikacja wymaga większej elastyczności niż zapewniana przez **_CrtDbgReport** i **_CrtDbgReportW**, można napisać własną funkcję raportowania i podłączyć ją do mechanizmu raportowania biblioteki wykonawczej C przy użyciu [_CrtSetReportHook](crtsetreporthook.md) funkcyjn.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtDbgReport**|\<crtdbg.h>|
|**_CrtDbgReportW**|\<crtdbg.h>|

**_CrtDbgReport** i **_CrtDbgReportW** są rozszerzeniami firmy Microsoft. Aby uzyskać więcej informacji, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje wyłącznie [bibliotek uruchomieniowych C](../../c-runtime-library/crt-library-features.md) .

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

Zobacz [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2) , aby zapoznać się z przykładem sposobu zmiany funkcji raportu.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportMode](crtsetreportmode.md)<br/>
[_CrtSetReportFile](crtsetreportfile.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
