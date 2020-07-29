---
title: _ASSERT, _ASSERTE, _ASSERT_EXPR makra
ms.date: 11/04/2016
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
- _ASSERTE
- ASSERTE
- _ASSERT_EXPR
helpviewer_keywords:
- debugging [CRT], using macros
- _ASSERTE macro
- macros, debugging with
- debug reporting macros
- _ASSERT macro
- _ASSERT_EXPR macro
ms.assetid: e98fd2a6-7f5e-4aa8-8fe8-e93490deba36
ms.openlocfilehash: d07fbe5de7afdc62f952727660447c5e4f0b78aa
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232641"
---
# <a name="_assert-_asserte-_assert_expr-macros"></a>_ASSERT, _ASSERTE, _ASSERT_EXPR makra

Oceń wyrażenie i Wygeneruj raport debugowania, gdy wynik ma **wartość false** (tylko wersja Debug).

## <a name="syntax"></a>Składnia

```C
// Typical usage:
_ASSERT_EXPR( booleanExpression, message );
_ASSERT( booleanExpression );
_ASSERTE( booleanExpression );
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Wyrażenie skalarne (w tym wyrażenia wskaźnika), które ma wartość różną od zera (true) lub 0 (false).

*Komunikat*<br/>
Szeroki ciąg, który ma być wyświetlany jako część raportu.

## <a name="remarks"></a>Uwagi

Makra **_ASSERT_EXPR**, **_ASSERT** i **_ASSERTE** zapewniają aplikację z czystym i prostym mechanizmem do sprawdzania założeń w procesie debugowania. Są one bardzo elastyczne, ponieważ nie muszą być ujęte w `#ifdef` instrukcje, aby uniemożliwić ich wywoływanie w ramach kompilacji detalicznej aplikacji. Tę elastyczność uzyskuje się za pomocą makra [_DEBUG](../../c-runtime-library/debug.md) . **_ASSERT_EXPR**, **_ASSERT** i **_ASSERTE** są dostępne tylko wtedy, gdy **_DEBUG** jest zdefiniowana w czasie kompilacji. Gdy **_DEBUG** nie jest zdefiniowany, wywołania tych makr są usuwane podczas przetwarzania wstępnego.

**_ASSERT_EXPR**, **_ASSERT** i **_ASSERTE** Oceń swój argument *booleanExpression* i kiedy wynik wynosi **`false`** (0), drukuje komunikat diagnostyczny i Wywołaj [_CrtDbgReportW](crtdbgreport-crtdbgreportw.md) , aby wygenerować raport debugowania. Makro **_ASSERT** drukuje prosty komunikat diagnostyczny, **_ASSERTE** zawiera ciąg reprezentujący wyrażenie zakończone niepowodzeniem w komunikacie, a **_ASSERT_EXPR** zawiera ciąg *komunikatu* w komunikacie diagnostycznym. Te makra nie wykonują żadnych operacji, gdy *booleanExpression* oblicza wartość różną od zera.

**_ASSERT_EXPR**, **_ASSERT** i **_ASSERTE** Invoke **_CrtDbgReportW**, co powoduje, że wszystkie dane wyjściowe powinny być w postaci szerokich znaków. **_ASSERTE** prawidłowo drukuje znaki Unicode w *booleanExpression* i **_ASSERT_EXPR** drukuje znaki Unicode w *wiadomości*.

Ponieważ **_ASSERTE** makro określa wyrażenie zakończone niepowodzeniem, a **_ASSERT_EXPR** pozwala określić komunikat w wygenerowanym raporcie, umożliwiają użytkownikom identyfikację problemu bez odwoływania się do kodu źródłowego aplikacji. Jednak istnieje wada, że każdy *komunikat* wydrukowany przez **_ASSERT_EXPR** i każde wyrażenie oceniane przez **_ASSERTE** jest zawarty w pliku danych wyjściowych (debugowania wersji) aplikacji jako stała ciąg. W związku z tym, jeśli wiele wywołań zostanie wykonanych do **_ASSERT_EXPR** lub **_ASSERTE**, wyrażenia te mogą znacznie zwiększyć rozmiar pliku wyjściowego.

O ile nie określisz inaczej z funkcjami [_CrtSetReportMode](crtsetreportmode.md) i [_CrtSetReportFile](crtsetreportfile.md) , komunikaty są wyświetlane w oknie dialogowym podręcznym równym ustawieniu:

```C
_CrtSetReportMode(CRT_ASSERT, _CRTDBG_MODE_WNDW);
````

**_CrtDbgReportW** generuje raport debugowania i określa jego miejsce docelowe lub lokalizacje docelowe w oparciu o bieżący tryb raportu lub tryby i plik zdefiniowany dla typu raportu **_CRT_ASSERT** . Domyślnie błędy i błędy potwierdzenia są kierowane do okna komunikatu debugowania. Funkcje [_CrtSetReportMode](crtsetreportmode.md) i [_CrtSetReportFile](crtsetreportfile.md) służą do definiowania miejsc docelowych dla każdego typu raportu.

Gdy miejscem docelowym jest okno komunikatu debugowania, a użytkownik kliknie przycisk **Ponów próbę** , **_CrtDbgReportW** zwraca wartość 1, co spowoduje, że **_ASSERT_EXPR**, **_ASSERT** i **_ASSERTE** makra do uruchomienia debugera, pod warunkiem że włączone jest debugowanie just-in-Time (JIT).

Aby uzyskać więcej informacji na temat procesu raportowania, zobacz [_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md) funkcji. Aby uzyskać więcej informacji na temat rozwiązywania błędów potwierdzenia i używania tych makr jako mechanizmu obsługi błędów debugowania, zobacz [Używanie makr do weryfikacji i raportowania](/visualstudio/debugger/macros-for-reporting).

Oprócz makr **_ASSERT** , makro [Assert](assert-macro-assert-wassert.md) może służyć do weryfikowania logiki programu. To makro jest dostępne zarówno w wersji Debug, jak i Release. [_RPT, _RPTF](rpt-rptf-rptw-rptfw-macros.md) makra debugowania są również dostępne do generowania raportu debugowania, ale nie obliczają wyrażenia. Makra **_RPT** generują prosty raport. Makra **_RPTF** zawierają plik źródłowy i numer wiersza, w którym makro raportu zostało wywołane w wygenerowanym raporcie. Dostępne są wersje szerokiego znaku tych makr (**_RPTW**, **_RPTFW**). Wersje o szerokim znaku są identyczne z wersjami znaków wąskich, z wyjątkiem tego, że ciągi znaków dwubajtowych są używane dla wszystkich parametrów ciągów i danych wyjściowych.

Mimo że **_ASSERT_EXPR**, **_ASSERT** i **_ASSERTE** są makrami i są dostępne przez włączenie \<crtdbg.h> , aplikacja musi łączyć się z wersją debugowania biblioteki wykonawczej C, gdy **_DEBUG** jest zdefiniowana, ponieważ te makra wywołują inne funkcje czasu wykonywania.

## <a name="requirements"></a>Wymagania

|Makro|Wymagany nagłówek|
|-----------|---------------------|
|**_ASSERT_EXPR**, **_ASSERT**, **_ASSERTE**|\<crtdbg.h>|

## <a name="example"></a>Przykład

W tym programie wywołania są wykonywane do **_ASSERT** i **_ASSERTE** makra w celu przetestowania warunku `string1 == string2` . Jeśli warunek nie powiedzie się, te makra drukują komunikat diagnostyczny. **_RPT** i **_RPTF** grupy makr są również wykonywane w tym programie jako alternatywa dla funkcji **printf** .

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
[potwierdzj makro, _assert, _wassert](assert-macro-assert-wassert.md)<br/>
[_RPT, _RPTF, _RPTW, _RPTFW makra](rpt-rptf-rptw-rptfw-macros.md)<br/>
