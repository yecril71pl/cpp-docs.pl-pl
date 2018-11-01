---
title: _CrtSetReportFile
ms.date: 11/04/2016
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
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
ms.openlocfilehash: 32a560e09c47468daf48c185e23d6e289c6d1d9b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464249"
---
# <a name="crtsetreportfile"></a>_CrtSetReportFile

Po użyciu [_CrtSetReportMode](crtsetreportmode.md) do określenia **_CRTDBG_MODE_FILE**, można określić dojście do pliku, aby otrzymać tekst wiadomości. **_CrtSetReportFile** jest również używany przez [_CrtDbgReport, _crtdbgreportw —](crtdbgreport-crtdbgreportw.md) Aby określić miejsce docelowe tekstu (tylko wersja debugowania).

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

Po pomyślnym zakończeniu **_CrtSetReportFile** zwraca poprzedni plik raportu zdefiniowany dla określony typu raportu w *reportType*. Jeśli nieprawidłowa wartość jest przekazywana do *reportType*, funkcja wywoła procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** a funkcja zwraca **_CRTDBG_HFILE_ERROR**. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_CrtSetReportFile** jest używana z [_CrtSetReportMode](crtsetreportmode.md) funkcji do określenia miejsca lub miejsc docelowych dla określonego typu raportu generowanego przez **_CrtDbgReport**. Gdy **_CrtSetReportMode** została wywołana do przypisania **_CRTDBG_MODE_FILE** tryb raportowania dla określonego typu raportu, **_CrtSetReportFile** powinien być wywoływany w celu Zdefiniuj określonego pliku lub strumienia mającego służyć jako miejsce docelowe. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtSetReportFile** są usuwane podczas przetwarzania wstępnego.

Na poniższej liście przedstawiono dostępne opcje *reportFile* i zachowanie wynikową **_CrtDbgReport**. Te opcje są zdefiniowane jako flaga bitowych w Crtdbg.h.

- **dojście do pliku**

   Dojście do pliku, który będzie miejsce docelowe dla wiadomości. Aby sprawdzić poprawność uchwyt jest podejmowana próba. Należy otworzyć i zamknąć dojście do pliku. Na przykład:

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

   Wpisuje wiadomość do **stderr**, które mogą zostać przekierowane w następujący sposób:

   ```C
   freopen( "c:\\log2.txt", "w", stderr);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);

   _RPT0(_CRT_ERROR,"1st message\n");
   ```

- **_CRTDBG_FILE_STDOUT**

   Wpisuje wiadomość do **stdout**, który można przekierować.

- **_CRTDBG_REPORT_FILE**

   Zwraca bieżący tryb raportu.

Plikiem raportu używanym przez każdy typu raportu można sterować oddzielnie. Na przykład, istnieje możliwość określić, że *reportType* z **_CRT_ERROR** zgłaszane **strumienia wyjściowego stderr**, podczas gdy *reportType* z **_CRT_ASSERT** zgłaszane dojście do zdefiniowanych przez użytkownika pliku lub strumienia.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_CrtSetReportFile**|\<crtdbg.h>|\<errno.h>|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej Windows (UWP). Standardowe uchwyty strumienia, które są powiązane z konsolą, **stdin**, **stdout**, i **stderr**, muszą zostać przekierowane zanim funkcje środowiska wykonawczego języka C można ich używać w aplikacjach platformy UWP . Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

**Biblioteki:** Debuguj wersje [funkcje biblioteki CRT](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
