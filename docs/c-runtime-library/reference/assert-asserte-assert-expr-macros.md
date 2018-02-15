---
title: "_ASSERT, _asserte —, _ASSERT_EXPR makra | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b5dae684d922287c1301338ed3a59844ff6313ac
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="assert-asserte-assertexpr-macros"></a>_ASSERT, _asserte —, _ASSERT_EXPR makra
Oceń wyrażenia i Generowanie raportu debugowania, gdy wynik jest `False` (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
_ASSERT_EXPR(  
   booleanExpression,  
   message  
);  
_ASSERT(   
   booleanExpression   
);  
_ASSERTE(   
   booleanExpression   
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `booleanExpression`  
 Wyrażenie skalarne (w tym wyrażenia wskaźnika), którego wynikiem jest różna od zera (true) lub wpisz 0 (false).  
  
 `message`  
 Ciąg typu wide do wyświetlenia w ramach raportu.  
  
## <a name="remarks"></a>Uwagi  
 `_ASSERT_EXPR`, `_ASSERT` i `_ASSERTE` makra dostarczać czyste i proste mechanizmu sprawdzania założenia podczas debugowania aplikacji. Są one bardzo elastyczne, ponieważ nie muszą być ujęte w `#ifdef` instrukcje, aby uniemożliwić ich wywołana w sprzedaży detalicznej kompilacji aplikacji. Tego rodzaju elastyczności jest realizowane za pośrednictwem [_DEBUG](../../c-runtime-library/debug.md) makra. `_ASSERT_EXPR`, `_ASSERT` i `_ASSERTE` są dostępne tylko podczas `_DEBUG` jest definiowany w czasie kompilacji. Gdy `_DEBUG` jest niezdefiniowana, wywołań do tych makr są usuwane podczas przetwarzania wstępnego.  
  
 `_ASSERT_EXPR`, `_ASSERT` i `_ASSERTE` oceny ich `booleanExpression` argument, a wynik jest `false` (0), drukowania komunikatów diagnostycznych i wywołanie [_crtdbgreportw —](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) do wygenerowania raportu debugowania. `_ASSERT` Makro drukuje wiadomość diagnostycznych proste `_ASSERTE` obejmuje reprezentację ciągu wyrażenia nie powiodło się w komunikacie, i `_ASSERT_EXPR` obejmuje `message` ciągu w komunikacie diagnostycznych. Nic nie rób tych makr podczas `booleanExpression` jest różna od zera.  
  
 `_ASSERT_EXPR`, `_ASSERT` i `_ASSERTE` wywołania `_CrtDbgReportW`, co powoduje, że wszystkie dane wyjściowe w znaki dwubajtowe. `_ASSERTE` Wyświetla prawidłowe znaki Unicode w `booleanExpression` i `_ASSERT_EXPR` drukuje znaki Unicode w `message`.  
  
 Ponieważ `_ASSERTE` makro określa wyrażenie nie powiodło się i `_ASSERT_EXPR` pozwala określić komunikat w generowanym raporcie, pozwalają użytkownikom na identyfikację problem bez odwołujących się do kodu źródłowego aplikacji. Jednak wadą istnieje w tym co `message` drukowanymi przez `_ASSERT_EXPR` i co wyrażenia obliczonego przy `_ASSERTE` znajduje się w pliku wyjściowym (wersja do debugowania) aplikacji jako stałą typu string. W związku z tym jeśli dużej liczby wywołań do `_ASSERT_EXPR` lub `_ASSERTE`, wyrażenia te mogą znacznie zwiększyć rozmiar pliku wyjściowego.  
  
 Jeśli nie określono inaczej z [_crtsetreportmode —](../../c-runtime-library/reference/crtsetreportmode.md) i [_crtsetreportfile —](../../c-runtime-library/reference/crtsetreportfile.md) funkcji, komunikaty są wyświetlane w oknie dialogowym wyskakujących odpowiednikiem ustawienia:  
  
`_CrtSetReportMode(CRT_ASSERT, _CRTDBG_MODE_WNDW);`  
  
 `_CrtDbgReportW` generuje raport debugowania i określa jego przeznaczenia lub miejsc docelowych, na podstawie bieżący tryb raportu lub tryby i zdefiniowana dla pliku `_CRT_ASSERT` typ raportu. Domyślnie błędy potwierdzenia i błędów są przekierowywane do okna komunikatu debugowania. [_Crtsetreportmode —](../../c-runtime-library/reference/crtsetreportmode.md) i [_crtsetreportfile —](../../c-runtime-library/reference/crtsetreportfile.md) funkcje są używane do definiowania miejsc docelowych dla każdego typu raportu.  
  
 Jeśli obiektem docelowym jest użytkownika i debugowania okna komunikatu kliknie **ponów** przycisku, `_CrtDbgReportW` zwraca wartość 1, powoduje `_ASSERT_EXPR`, `_ASSERT` i `_ASSERTE` makra można uruchomić debugera, pod warunkiem, że włączone jest debugowanie just-in-time (JIT).  
  
 Aby uzyskać więcej informacji na temat procesu raportowania patrz [_crtdbgreport —, _crtdbgreportw —](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) funkcji. Aby uzyskać więcej informacji na temat rozpoznawania błędy potwierdzenia i używania tych makr jako błąd debugowania mechanizmu obsługi, zobacz [przy użyciu makra weryfikacji i raportowania](/visualstudio/debugger/macros-for-reporting).  
  
 Oprócz `_ASSERT` makra, [assert](../../c-runtime-library/reference/assert-macro-assert-wassert.md) makro może służyć do Sprawdź logice programu. To makro jest dostępna w debug i release wersje bibliotek. [_RPT, _RPTF](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) makra debugowania są także dostępne podczas generowania raportu debugowania, ale nie oceniają wyrażenia. `_RPT` Makra wygenerować prosty raport. `_RPTF` Makra włączyć do źródła plików i wierszy której wywołano makro raportu wygenerowanego raportu. Dostępne są wersje tych makr znaków dwubajtowych (`_RPTWn`, `_RPTFWn`). Wersje znaków dwubajtowych są takie same jak wersje znaki wąskie, z wyjątkiem tego, że wszystkie parametry ciągu i dane wyjściowe są używane ciągi znaków dwubajtowych.  
  
 Mimo że `_ASSERT_EXPR`, `_ASSERT` i `_ASSERTE` są makra i są dostępne przy tym \<crtdbg.h >, połączyć z wersja biblioteki wykonawczej języka C do debugowania aplikacji podczas `_DEBUG` jest zdefiniowana, ponieważ wywołania tych makr inne funkcje czasu wykonywania.  
  
## <a name="requirements"></a>Wymagania  
  
|Macro|Wymagany nagłówek|  
|-----------|---------------------|  
|`_ASSERT_EXPR`,                  `_ASSERT`, `_ASSERTE`|\<crtdbg.h>|  
  
## <a name="example"></a>Przykład  
 W tym programie wywołań do `_ASSERT` i `_ASSERTE` makra testować warunek `string1 == string2`. Jeśli warunek nie powiedzie się, te makra drukowania diagnostycznych wiadomości. `_RPTn` i `_RPTFn` grupy makr również jest wykonywane w tym programie zamiast `printf` funkcji.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)   
 [assert Macro, _assert, _wassert](../../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [_RPT, _RPTF, _RPTW, _RPTFW Macros](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)