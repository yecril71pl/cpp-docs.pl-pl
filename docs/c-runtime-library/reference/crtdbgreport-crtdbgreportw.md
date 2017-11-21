---
title: "_Crtdbgreport —, _crtdbgreportw — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- debug reporting
- _CrtDbgReport function
- CrtDbgReport function
- CrtDbgReportW function
- _CrtDbgReportW function
ms.assetid: 6e581fb6-f7fb-4716-9432-f0145d639ecc
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bdd8d1545445ea6a478e065dbc3bb5a713e1a602
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="crtdbgreport-crtdbgreportw"></a>_CrtDbgReport, _CrtDbgReportW
Generuje raport z komunikatem debugowania i wysyła raport do trzech miejsc docelowych możliwe (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `reportType`  
 Typ raportu: `_CRT_WARN`, `_CRT_ERROR`, i `_CRT_ASSERT`.  
  
 `filename`  
 Wskaźnik do nazwy pliku źródłowego, w którym wystąpił assert raportu lub `NULL`.  
  
 `linenumber`  
 Numer wiersza na plik źródłowy, na którym wystąpił assert raportu lub `NULL`.  
  
 `moduleName`  
 Wskaźnik do nazwy modułu (.exe lub .dll) gdzie assert lub wystąpił raportu.  
  
 `format`  
 Wskaźnik do sterowania format ciąg używany do tworzenia komunikat.  
  
 `argument`  
 Argumenty opcjonalne podstawienia używane przez `format`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Dla wszystkich raportów miejsc docelowych `_CrtDbgReport` i `_CrtDbgReportW` Zwróć -1, jeśli wystąpi błąd i 0, jeśli nie zostaną napotkane żadne błędy. Jednak gdy raport docelowy jest użytkownika i debugowania okna komunikatu kliknie **ponów** przycisku Funkcje zwracają 1. Gdy użytkownik kliknie **przerwać** przycisk w oknie komunikatu debugowania tych funkcji natychmiast przerwania i nie zwraca wartości.  
  
 [_RPT, _RPTF](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) debugowania wywołanie makra `_CrtDbgReport` do ich debugowania generowania raportów. Wersje znaków dwubajtowych tych makr oraz [_ASSERT &#91; W &#93; ](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), `_RPTW n` i `_RPTFW n`, użyj `_CrtDbgReportW` do ich debugowania generowania raportów. Gdy `_CrtDbgReport` lub `_CrtDbgReportW` zwraca 1, te makra uruchomienia debugera, pod warunkiem, że włączone jest debugowanie just-in-time (JIT).  
  
## <a name="remarks"></a>Uwagi  
 `_CrtDbgReport`i `_CrtDbgReportW` wysłać raport debugowania do trzech różnych miejsc docelowych: plik raportu debugowania, monitor debugowania ( [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] debugera), lub w oknie komunikatu debugowania. Dwie funkcje konfiguracji, [_crtsetreportmode —](../../c-runtime-library/reference/crtsetreportmode.md) i [_crtsetreportfile —](../../c-runtime-library/reference/crtsetreportfile.md), są używane do określenia przeznaczenia lub miejsc docelowych dla każdego typu raportu. Te funkcje umożliwiają raportowania docelowego lub miejsc docelowych dla każdego typu raportu można sterować oddzielnie. Na przykład użytkownik może określić, że `reportType` z `_CRT_WARN` tylko wysyłane do monitora debugowania, podczas gdy `reportType` z `_CRT_ASSERT` wysłane do pliku raportu zdefiniowane przez użytkownika i debugowania okna komunikatu.  
  
 `_CrtDbgReportW`jest to wersja znaków dwubajtowych `_CrtDbgReport`. Wszystkie jej dane wyjściowe i ciąg parametry są w ciągach znaków dwubajtowych; w przeciwnym razie jest taka sama jak wersja znaków.  
  
 `_CrtDbgReport`i `_CrtDbgReportW` utworzyć komunikat raportu debugowania podstawiając `argument`[`n`] argumenty do `format` ciąg znaków, według reguł zdefiniowanych przez `printf` lub `wprintf` funkcji. Te funkcje następnie wygeneruj raport debugowania i określenia przeznaczenia lub miejsc docelowych, które są oparte na trybie Bieżące raportu i pliku zdefiniowane dla `reportType`. Gdy raport jest wysyłany do okna komunikatu debugowania, `filename`, `lineNumber`, i `moduleName` znajdują się informacje wyświetlane w oknie.  
  
 W poniższej tabeli wymieniono dostępne opcje dla trybie raportu lub trybów plików i zachowanie wynikowy `_CrtDbgReport` i `_CrtDbgReportW`. Te opcje są zdefiniowane jako flagi bitów w \<crtdbg.h >.  
  
|Tryb raportu|Plik raportu|`_CrtDbgReport`, `_CrtDbgReportW` zachowanie|  
|-----------------|-----------------|------------------------------------------------|  
|`_CRTDBG_MODE_DEBUG`|Nie dotyczy|Zapisuje komunikat przy użyciu systemu Windows [OutputDebugString](http://msdn.microsoft.com/library/windows/desktop/aa363362.aspx) interfejsu API.|  
|`_CRTDBG_MODE_WNDW`|Nie dotyczy|Wymaga systemu Windows [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) interfejsu API, aby utworzyć komunikat do wyświetlenia komunikatu, wraz z **przerwać**, **ponów**, i **Ignoruj** przycisków. Gdy użytkownik kliknie **przerwać**, `_CrtDbgReport` lub `_CrtDbgReport` natychmiastowe przerwanie. Gdy użytkownik kliknie **ponów**, zwraca 1. Gdy użytkownik kliknie **Ignoruj**, wykonanie jest kontynuowane i `_CrtDbgReport` i `_CrtDbgReportW` zwraca 0. Należy pamiętać, że kliknięcie pozycji **Ignoruj** gdy warunek błędu istnieje często skutkuje "niezdefiniowane zachowanie."|  
|`_CRTDBG_MODE_FILE`|`__HFILE`|Zapisuje komunikat do podanego użytkownika `HANDLE`, przy użyciu systemu Windows [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747.aspx) interfejsu API i nie sprawdza poprawność dojście do pliku; aplikacji jest odpowiedzialny za otwieranie pliku raportu i przekazywanie dojścia prawidłowy plik.|  
|`_CRTDBG_MODE_FILE`|`_CRTDBG_FILE_STDERR`|Zapisuje komunikat do `stderr`.|  
|`_CRTDBG_MODE_FILE`|`_CRTDBG_FILE_STDOUT`|Zapisuje komunikat do `stdout`.|  
  
 Raport mogą być wysyłane do jednego, dwóch lub trzech miejsc docelowych lub nie docelowego w ogóle. Aby uzyskać więcej informacji na temat określania trybu raportu lub tryby i plik raportu, zobacz [_crtsetreportmode —](../../c-runtime-library/reference/crtsetreportmode.md) i [_crtsetreportfile —](../../c-runtime-library/reference/crtsetreportfile.md) funkcji. Aby uzyskać więcej informacji o użyciu makra debugowania i funkcje raportowania, zobacz [makra dla raportowania](/visualstudio/debugger/macros-for-reporting).  
  
 Jeśli aplikacja wymaga większą elastyczność niż te dostarczone przez `_CrtDbgReport` i `_CrtDbgReportW`, możesz zapisać własnego raportowania funkcji i podłącz go do biblioteki wykonawcze języka C mechanizm raportowania przy użyciu [_crtsetreporthook —](../../c-runtime-library/reference/crtsetreporthook.md)funkcji.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_CrtDbgReport`|\<crtdbg.h >|  
|`_CrtDbgReportW`|\<crtdbg.h >|  
  
 `_CrtDbgReport`i `_CrtDbgReportW` są rozszerzenia Microsoft. Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wersja debugowania [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_crtdbgreport.c  
#include <crtdbg.h>  
  
int main(int argc, char *argv[]) {  
#ifdef _DEBUG  
   _CrtDbgReport(_CRT_ASSERT, __FILE__, __LINE__, argv[0], NULL);  
#endif  
}  
```  
  
 Zobacz [crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167) przykład sposobu zmiany funkcji raportu.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)   
 [_Crtsetreportmode —](../../c-runtime-library/reference/crtsetreportmode.md)   
 [_Crtsetreportfile —](../../c-runtime-library/reference/crtsetreportfile.md)   
 [printf, _printf_l —, wprintf, _wprintf_l —](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [_DEBUG](../../c-runtime-library/debug.md)