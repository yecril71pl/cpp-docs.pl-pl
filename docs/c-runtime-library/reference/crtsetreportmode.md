---
title: "_Crtsetreportmode — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 45319f7584d0c18533433d01b3467ccfeecac8df
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="crtsetreportmode"></a>_CrtSetReportMode
Określa docelowy lub miejsc docelowych dla typu określonego raportu generowane przez `_CrtDbgReport` i makr, które wywołują [_crtdbgreport —, _crtdbgreportw —](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md), takich jak [_ASSERT, _asserte —, makra _ASSERT_EXPR](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), [_ASSERT, _asserte —, makra _ASSERT_EXPR](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), [_RPT, _RPTF, _RPTW, _rptfw — makra](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md), i [_RPT, _RPTF, _RPTW, _rptfw — makra](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _CrtSetReportMode(   
   int reportType,  
   int reportMode   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `reportType`  
 Typ raportu: `_CRT_WARN`, `_CRT_ERROR`, i `_CRT_ASSERT`.  
  
 `reportMode`  
 Nowy tryb lub tryby raportu dla parametru `reportType`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Gdy funkcja `_CrtSetReportMode` zostanie wykonana pomyślnie, zwraca poprzedni tryb lub tryby raportu dla typu raportu określonego parametrem `reportType`. Jeśli wartość jest nieprawidłowa jest przekazywany jako `reportType` lub określono nieprawidłowy tryb `reportMode`, `_CrtSetReportMode` wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia `errno` do `EINVAL` i zwraca wartość -1. Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 Funkcja `_CrtSetReportMode` określa miejsce docelowe danych wyjściowych funkcji `_CrtDbgReport`. Ponieważ makra `_ASSERT`, `_ASSERTE`, `_RPT` i `_RPTF` wywołują funkcję `_CrtDbgReport`, funkcja `_CrtSetReportMode` określa lokalizację wyjściową tekstu objętego makrami.  
  
 Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań `_CrtSetReportMode` są usuwane podczas przetwarzania wstępnego.  
  
 Jeśli w celu zdefiniowania lokalizacji wyjściowej komunikatów nie zostanie wywołana funkcja `_CrtSetReportMode`, obowiązują następujące domyślne lokalizacje:  
  
-   Błędy potwierdzeń są kierowane do okna komunikatów debugowania.  
  
-   Ostrzeżenia z aplikacji systemu Windows są wysyłane do okna danych wyjściowych debugera.  
  
-   Ostrzeżenia z aplikacji konsolowych nie są wyświetlane.  
  
 Poniższa tabela zawiera listę typów raportów zdefiniowanych w pliku Crtdbg.h.  
  
|Typ raportu|Opis|  
|-----------------|-----------------|  
|`_CRT_WARN`|Ostrzeżenia, komunikaty i informacje, które nie wymagają natychmiastowej uwagi.|  
|`_CRT_ERROR`|Błędy, nieodwracalne problemy i kwestie, które wymagają natychmiastowej uwagi.|  
|`_CRT_ASSERT`|Błędy potwierdzeń (wyrażenia potwierdzeń, które dają w wyniku `FALSE`).|  
  
 Funkcja `_CrtSetReportMode` przypisuje nowy tryb raportu określony w parametrze `reportMode` do typu raportu określonego w parametrze `reportType`, a następnie zwraca tryb raportu uprzednio zdefiniowany w parametrze `reportType`. W poniższej tabeli przedstawiono listę dostępnych opcji `reportMode` oraz wynikowe zachowania funkcji `_CrtDbgReport`. Te opcje są definiowane jako flagi bitów w Crtdbg.h.  
  
|Tryb raportu|Zachowanie funkcji _CrtDbgReport|  
|-----------------|-----------------------------|  
|`_CRTDBG_MODE_DEBUG`|Zapisywanie komunikatu w oknie danych wyjściowych debugera.|  
|`_CRTDBG_MODE_FILE`|Zapisywanie komunikatu w dojściu do pliku wskazanym przez użytkownika. [_Crtsetreportfile —](../../c-runtime-library/reference/crtsetreportfile.md) powinna być wywoływana w celu zdefiniowania określonego pliku lub strumienia ma być używana jako miejsce docelowe.|  
|`_CRTDBG_MODE_WNDW`|Tworzenie okna komunikatu, wraz z przyciskami `Abort`, `Retry` i `Ignore`, w celu wyświetlenia komunikatu.|  
|`_CRTDBG_REPORT_MODE`|Zwracanie parametru `reportMode` dla podanego parametru `reportType`:<br /><br /> 1   `_CRTDBG_MODE_FILE`<br /><br /> 2   `_CRTDBG_MODE_DEBUG`<br /><br /> 4   `_CRTDBG_MODE_WNDW`|  
  
 Każdy typ raportu może być przekazywany przy użyciu jednego, dwóch lub trzech trybów albo bez żadnego trybu. Dlatego jeden typ raportu może mieć zdefiniowane więcej niż jedno miejsce docelowe. Na przykład poniższy fragment kodu powoduje wysłanie błędów potwierdzeń do okna komunikatów debugowania i do strumienia `stderr`:  
  
```  
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );  
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );  
```  
  
 Ponadto trybem lub trybami raportowania każdego typu raportu można sterować oddzielnie. Na przykład można określić, że `reportType``_CRT_WARN` będzie wysyłany do ciągu debugowania danych wyjściowych, podczas raport typu `_CRT_ASSERT` będzie wyświetlany w oknie komunikatów debugowania i wysyłany do strumienia `stderr`, jak przedstawiono wcześniej.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_CrtSetReportMode`|\<crtdbg.h>|\<errno.h>|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
 **Biblioteki:** wersja debugowania [Biblioteka CRT — funkcje](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)