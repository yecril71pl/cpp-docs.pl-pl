---
title: _ASSERT, _asserte —, makra _ASSERT_EXPR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
- _ASSERTE
- ASSERTE
- _ASSERT
- _ASSERT_EXPR
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], using macros
- _ASSERTE macro
- macros, debugging with
- debug reporting macros
- _ASSERT macro
- _ASSERT_EXPR macro
ms.assetid: e98fd2a6-7f5e-4aa8-8fe8-e93490deba36
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 254550acf94acb846826bc0efe76ef26753c54b8
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107593"
---
# <a name="assert-asserte-assertexpr-macros"></a>_ASSERT, _asserte —, _ASSERT_EXPR makra

Ocena wyrażenia i Generowanie raportu debugowania, gdy wynik jest **False** (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
// Typical usage:
_ASSERT_EXPR( booleanExpression, message );
_ASSERT( booleanExpression );
_ASSERTE( booleanExpression );
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Wyrażenie skalarne (w tym wyrażenia wskaźnika), którego wynikiem jest niezerowe (PRAWDA) lub 0 (false).

*komunikat*<br/>
Szeroki ciąg do wyświetlenia jako część raportu.

## <a name="remarks"></a>Uwagi

**_ASSERT_EXPR**, **_ASSERT** i **_asserte —** makra udostępniać prosty i przejrzysty mechanizmu sprawdzania założeń podczas debugowania aplikacji. Są one bardzo elastyczny, ponieważ nie muszą być ujęte w nawiasy `#ifdef` instrukcji, aby uniemożliwić ich wywoływana w przypadku kompilacji detalicznej aplikacji. Ta elastyczność to osiągnąć, używając [_DEBUG](../../c-runtime-library/debug.md) makra. **_ASSERT_EXPR**, **_ASSERT** i **_asserte —** są dostępne tylko w przypadku **_DEBUG** jest definiowany w czasie kompilacji. Gdy **_DEBUG** jest nie jest zdefiniowany, wywołania te makra są usuwane podczas przetwarzania wstępnego.

**_ASSERT_EXPR**, **_ASSERT** i **_asserte —** ocenić ich *booleanExpression* argument, a wynik jest **false**(0), wydrukowaniu komunikat diagnostyczny i wywołania [_crtdbgreportw —](crtdbgreport-crtdbgreportw.md) do wygenerowania raportu debugowania. **_ASSERT** — makro drukuje prosty komunikat diagnostyczny **_asserte —** zawiera ciąg reprezentujący wyrażenie nie powiodło się w wiadomości, a **_ASSERT_EXPR** obejmuje *komunikat* ciąg znaków w komunikacie dotyczącym diagnostyki. Te makra nic nie rób podczas *booleanExpression* daje w wyniku wartość różną od zera.

**_ASSERT_EXPR**, **_ASSERT** i **_asserte —** wywołania **_crtdbgreportw —**, co powoduje, że wszystkie dane wyjściowe w znaki dwubajtowe. **_Asserte —** prawidłowo Wyświetla znaki Unicode w *booleanExpression* i **_ASSERT_EXPR** Wyświetla znaki Unicode w *komunikat*.

Ponieważ **_asserte —** makro określa wyrażenie nie powiodło się i **_ASSERT_EXPR** pozwala określić komunikat w generowanym raporcie, pozwalają użytkownikom na identyfikację problemu bez odwołujące się do Kod źródłowy aplikacji. Jednak wadą istnieje w tym co *komunikat* drukowanymi przez **_ASSERT_EXPR** i każde wyrażenie oceniane przez **_asserte —** znajduje się w danych wyjściowych (wersja debugowania) plik aplikacji jako stałą typu string. W związku z tym, jeśli dużej liczby wywołań do **_ASSERT_EXPR** lub **_asserte —**, te wyrażenia może znacznie zwiększyć rozmiar pliku wyjściowego.

Chyba że określono inaczej z [_CrtSetReportMode](crtsetreportmode.md) i [_CrtSetReportFile](crtsetreportfile.md) funkcje, komunikaty są wyświetlane w podręcznym oknie dialogowym równoważne ustawieniu:

```C
_CrtSetReportMode(CRT_ASSERT, _CRTDBG_MODE_WNDW);
````

**_Crtdbgreportw —** generuje raport debugowania i określa jej miejsca przeznaczenia lub miejsca, w oparciu o bieżący tryb raportu lub trybów i plik zdefiniowany dla **_CRT_ASSERT** typ raportu. Domyślnie błędy potwierdzeń są kierowane do okna komunikatów debugowania. [_CrtSetReportMode](crtsetreportmode.md) i [_CrtSetReportFile](crtsetreportfile.md) funkcje są używane do definiowania miejsca docelowe dla każdego typu raportu.

Gdy obiektem docelowym jest okna komunikatów debugowania i użytkownik klika polecenie **ponów próbę wykonania** przycisku **_crtdbgreportw —** zwraca wartość 1, co powoduje **_ASSERT_EXPR**, **_ ASERCJA** i **_asserte —** makra można uruchomić debugera, pod warunkiem, że włączone jest debugowanie just-in-time (JIT).

Aby uzyskać więcej informacji na temat raportowania procesu, zobacz [_CrtDbgReport, _crtdbgreportw —](crtdbgreport-crtdbgreportw.md) funkcji. Aby uzyskać więcej informacji o rozwiązywaniu problemów z niepowodzeniem asercji i jako mechanizm obsługi błędów debugowania przy użyciu tych makr, zobacz [używania makr do weryfikacji i raportowania](/visualstudio/debugger/macros-for-reporting).

Oprócz **_ASSERT** makra, [asercja](assert-macro-assert-wassert.md) — makro może służyć do Sprawdź logiki programu. To makro jest dostępna w debug i release wersje bibliotek. [_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) makr debugowania są również dostępne dla generowania raportu debugowania, ale nie oceniają wyrażenie. **_RPT** makra wygenerować prosty raport. **_RPTF** makra: źródło pliku i numer wiersza której wywołano makro raportów w generowanym raporcie. Dostępne są wersje szerokiego znaku tych makr (**_RPTW**, **_rptfw —**). Wersje szerokich znaków są identyczne z wersjami wąskiego znaku, z tą różnicą, że ciągi znaków dwubajtowych są używane dla wszystkich parametrów i danych wyjściowych.

Mimo że **_ASSERT_EXPR**, **_ASSERT** i **_asserte —** są makra, są dostępne, umieszczając \<crtdbg.h >, aplikacja musi łączyć się za pomocą debugowania wersji biblioteki wykonawczej C podczas **_DEBUG** jest zdefiniowana, ponieważ te makra wywołania innych funkcji wykonawczej.

## <a name="requirements"></a>Wymagania

|Macro|Wymagany nagłówek|
|-----------|---------------------|
|**_ASSERT_EXPR**, **_ASSERT**, **_ASSERTE —**|\<crtdbg.h>|

## <a name="example"></a>Przykład

W tym programie wywołaniach **_ASSERT** i **_asserte —** makra testować warunek `string1 == string2`. Jeśli warunek zakończy się niepowodzeniem, te makra wydrukuj komunikat diagnostyczny. **_RPT** i **_RPTF** grupy makr również jest wykonywane w tym programie jako alternatywę dla **printf** funkcji.

```C
// crt_ASSERT_macro.c
// compile with: /D_DEBUG /MTd /Od /Zi /link /verbose:lib /debug
//
// This program uses the _ASSERT and _ASSERTE debugging macros.
//

#include <stdio.h>
#include <string.h>
#include <malloc.h>
#include <crtdbg.h>

int main()
{
   char *p1, *p2;

   // The Reporting Mode and File must be specified
   // before generating a debug report via an assert
   // or report macro.
   // This program sends all report types to STDOUT.
   _CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_WARN, _CRTDBG_FILE_STDOUT);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDOUT);
   _CrtSetReportMode(_CRT_ASSERT, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ASSERT, _CRTDBG_FILE_STDOUT);

   // Allocate and assign the pointer variables.
   p1 = (char *)malloc(10);
   strcpy_s(p1, 10, "I am p1");
   p2 = (char *)malloc(10);
   strcpy_s(p2, 10, "I am p2");

   // Use the report macros as a debugging
   // warning mechanism, similar to printf.
   // Use the assert macros to check if the
   // p1 and p2 variables are equivalent.
   // If the expression fails, _ASSERTE will
   // include a string representation of the
   // failed expression in the report.
   // _ASSERT does not include the
   // expression in the generated report.
   _RPT0(_CRT_WARN,
       "Use the assert macros to evaluate the expression p1 == p2.\n");
   _RPTF2(_CRT_WARN, "\n Will _ASSERT find '%s' == '%s' ?\n", p1, p2);
   _ASSERT(p1 == p2);

   _RPTF2(_CRT_WARN, "\n\n Will _ASSERTE find '%s' == '%s' ?\n",
          p1, p2);
   _ASSERTE(p1 == p2);

   _RPT2(_CRT_ERROR, "'%s' != '%s'\n", p1, p2);

   free(p2);
   free(p1);

   return 0;
}
```

```Output
Use the assert macros to evaluate the expression p1 == p2.
crt_ASSERT_macro.c(54) :
Will _ASSERT find 'I am p1' == 'I am p2' ?
crt_ASSERT_macro.c(55) : Assertion failed!
crt_ASSERT_macro.c(58) :

Will _ASSERTE find 'I am p1' == 'I am p2' ?
crt_ASSERT_macro.c(59) : Assertion failed: p1 == p2
'I am p1' != 'I am p2'
```

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[assert Macro, _assert, _wassert](assert-macro-assert-wassert.md)<br/>
[_RPT, _RPTF, _RPTW, _RPTFW Macros](rpt-rptf-rptw-rptfw-macros.md)<br/>
