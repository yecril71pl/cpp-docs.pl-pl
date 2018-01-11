---
title: "_Crtsetreportfile — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _CrtSetReportFile
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
- CrtSetReportFile
- _CrtSetReportFile
dev_langs: C++
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8487ca011355ad248bc38c2fc2d3265f0fad4995
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="crtsetreportfile"></a>_CrtSetReportFile
Po użyciu [_crtsetreportmode —](../../c-runtime-library/reference/crtsetreportmode.md) do określenia `_CRTDBG_MODE_FILE`, można określić dojście do pliku do odbierania tekst komunikatu. `_CrtSetReportFile`jest już używana przez [_crtdbgreport —, _crtdbgreportw —](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) do określenia lokalizacji tekstu (tylko wersja do debugowania).  
  
## <a name="syntax"></a>Składnia  
  
```  
_HFILE _CrtSetReportFile(   
   int reportType,  
   _HFILE reportFile   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `reportType`  
 Typ raportu: `_CRT_WARN`, `_CRT_ERROR`, i `_CRT_ASSERT`.  
  
 `reportFile`  
 Nowy plik raportu dla `reportType`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Po pomyślnym ukończeniu `_CrtSetReportFile` zwraca poprzedniego pliku raportu zdefiniowane dla określonego typu raportu w `reportType`. Jeśli do została przekazana nieprawidłowa wartość `reportType`, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ustawiono `EINVAL` i funkcja zwraca `_CRTDBG_HFILE_ERROR`. Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `_CrtSetReportFile`jest używany z [_crtsetreportmode —](../../c-runtime-library/reference/crtsetreportmode.md) funkcji, aby zdefiniować docelowy lub miejsc docelowych dla typu określonego raportu generowane przez `_CrtDbgReport`. Gdy `_CrtSetReportMode` została wywołana można przypisać `_CRTDBG_MODE_FILE` raportowania tryb dla typu określonego raportu `_CrtSetReportFile` następnie powinna być wywoływana w celu zdefiniowania określonego pliku lub strumienia ma być używana jako miejsce docelowe. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań `_CrtSetReportFile` są usuwane podczas przetwarzania wstępnego.  
  
 W poniższej tabeli przedstawiono listę dostępnych sposobów `reportFile` i wynikowy zachowania `_CrtDbgReport`. Te opcje są definiowane jako flagi bitów w Crtdbg.h.  
  
 `file handle`  
 Dojście do pliku, który ma być miejsce docelowe dla wiadomości. Nie są podejmowane próby poprawność dojście. Należy otworzyć i zamknąć dojścia do pliku. Na przykład:  
  
```  
HANDLE hLogFile;  
hLogFile = CreateFile("c:\\log.txt", GENERIC_WRITE,   
   FILE_SHARE_WRITE, NULL, CREATE_ALWAYS,   
   FILE_ATTRIBUTE_NORMAL, NULL);  
_CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);  
_CrtSetReportFile(_CRT_WARN, hLogFile);  
  
_RPT0(_CRT_WARN,"file message\n");  
CloseHandle(hLogFile);  
```  
  
 `_CRTDBG_FILE_STDERR`  
 Zapisuje komunikat do `stderr`, które mogą zostać przekierowane w następujący sposób:  
  
```  
freopen( "c:\\log2.txt", "w", stderr);  
_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);  
_CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);  
  
_RPT0(_CRT_ERROR,"1st message\n");  
```  
  
 `_CRTDBG_FILE_STDOUT`  
 Zapisuje komunikat do `stdout`, które można przekierować.  
  
 `_CRTDBG_REPORT_FILE`  
 Zwraca bieżący tryb raportu.  
  
 Plik raportu używane przez każdego typu raportu można kontrolować osobno. Na przykład użytkownik może określić, że `reportType` z `_CRT_ERROR` zgłaszane `stderr`, gdy `reportType` z `_CRT_ASSERT` zgłaszane dojście do pliku zdefiniowane przez użytkownika lub strumienia.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_CrtSetReportFile`|\<crtdbg.h >|\<errno.h >|  
  
 Konsola nie jest obsługiwana w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu —`stdin`, `stdout`, i `stderr`— muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji. Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
 **Biblioteki:** wersja debugowania [Biblioteka CRT — funkcje](../../c-runtime-library/crt-library-features.md) tylko.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury debugowania](../../c-runtime-library/debug-routines.md)