---
title: _Crtsetreportfile — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtSetReportFile
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
dev_langs:
- C++
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3df4f54ad8e191dac7110a914bdde1cec888ff9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402341"
---
# <a name="crtsetreportfile"></a>_CrtSetReportFile

Po użyciu [_crtsetreportmode —](crtsetreportmode.md) do określenia **_CRTDBG_MODE_FILE**, można określić dojście do pliku do odbierania tekst komunikatu. **_Crtsetreportfile —** jest już używana przez [_crtdbgreport —, _crtdbgreportw —](crtdbgreport-crtdbgreportw.md) do określenia lokalizacji tekstu (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
_HFILE _CrtSetReportFile(
   int reportType,
   _HFILE reportFile
);
```

### <a name="parameters"></a>Parametry

*reportType*<br/>
Typ raportu: **_CRT_WARN**, **_CRT_ERROR**, i **_CRT_ASSERT**.

*reportFile*<br/>
Nowy plik raportu dla *reportType*.

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym ukończeniu **_crtsetreportfile —** zwraca poprzedniego pliku raportu zdefiniowane dla określonego typu raportu w *reportType*. Jeśli do została przekazana nieprawidłowa wartość *reportType*, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —** i funkcja zwraca **_CRTDBG_HFILE_ERROR**. Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Crtsetreportfile —** jest używany z [_crtsetreportmode —](crtsetreportmode.md) funkcji, aby zdefiniować docelowy lub miejsc docelowych dla typu określonego raportu generowane przez **_crtdbgreport —**. Gdy **_crtsetreportmode —** została wywołana można przypisać **_CRTDBG_MODE_FILE** raportowania tryb dla typu określonego raportu **_crtsetreportfile —** następnie powinna być wywoływana na Zdefiniuj określonego pliku lub strumienia ma być używana jako miejsce docelowe. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołań **_crtsetreportfile —** są usuwane podczas przetwarzania wstępnego.

Na poniższej liście przedstawiono dostępne opcje dla *reportFile* i wynikowy zachowania **_crtdbgreport —**. Te opcje są definiowane jako flagi bitów w Crtdbg.h.

- **dojście do pliku**

   Dojście do pliku, który ma być miejsce docelowe dla wiadomości. Nie są podejmowane próby poprawność dojście. Należy otworzyć i zamknąć dojścia do pliku. Na przykład:

   ```C
   HANDLE hLogFile;
   hLogFile = CreateFile("c:\\log.txt", GENERIC_WRITE,
      FILE_SHARE_WRITE, NULL, CREATE_ALWAYS,
      FILE_ATTRIBUTE_NORMAL, NULL);
   _CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_WARN, hLogFile);

   _RPT0(_CRT_WARN,"file message\n");
   CloseHandle(hLogFile);
   ```

- **_CRTDBG_FILE_STDERR**

   Zapisuje komunikat do **stderr**, które mogą zostać przekierowane w następujący sposób:

   ```C
   freopen( "c:\\log2.txt", "w", stderr);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);

   _RPT0(_CRT_ERROR,"1st message\n");
   ```

- **_CRTDBG_FILE_STDOUT**

   Zapisuje komunikat do **stdout**, które można przekierować.

- **_CRTDBG_REPORT_FILE**

   Zwraca bieżący tryb raportu.

Plik raportu używane przez każdego typu raportu można kontrolować osobno. Na przykład użytkownik może określić, że *reportType* z **_CRT_ERROR** zgłaszane **stderr**, podczas gdy *reportType* z **_CRT_ASSERT** zgłaszane dojście do pliku zdefiniowane przez użytkownika lub strumienia.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_CrtSetReportFile**|\<crtdbg.h>|\<errno.h>|

Konsoli nie jest obsługiwane w aplikacjach systemu Windows platformy Uniwersalnej. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu **stdin**, **stdout**, i **stderr**, muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w aplikacji platformy uniwersalnej systemu Windows . Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

**Biblioteki:** wersja debugowania [Biblioteka CRT — funkcje](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
