---
title: _spawnvp, _wspawnvp
ms.date: 11/04/2016
api_name:
- _wspawnvp
- _spawnvp
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
- api-ms-win-crt-process-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wspawnvp
- _spawnvp
- wspawnvp
helpviewer_keywords:
- wspawnvp function
- processes, creating
- _wspawnvp function
- processes, executing new
- spawnvp function
- process creation
- _spawnvp function
ms.assetid: 8d8774ec-6ad4-4680-a5aa-440cde1e0249
ms.openlocfilehash: 8c54de21c2bfac693b3555c86eea98a32f132576
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958079"
---
# <a name="_spawnvp-_wspawnvp"></a>_spawnvp, _wspawnvp

Tworzy proces i wykonuje go.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
intptr_t _spawnvp(
   int mode,
   const char *cmdname,
   const char *const *argv
);
intptr_t _wspawnvp(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *const *argv
);
```

### <a name="parameters"></a>Parametry

*wyst*<br/>
Tryb wykonywania na potrzeby wywoływania procesu.

*cmdname*<br/>
Ścieżka pliku, który ma zostać wykonany.

*argv*<br/>
Tablica wskaźników do argumentów. Argument *argv*[0] jest zwykle wskaźnikiem do ścieżki w trybie rzeczywistym lub do nazwy programu w trybie chronionym, a *argv*[1] do *argv*[**n**] są wskaźnikami do ciągów znaków, które tworzą nową listę argumentów. Argument *argv*[**n** + 1] musi być **pustym** wskaźnikiem, aby zaznaczyć koniec listy argumentów.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana z synchronicznego **_spawnvp** lub **_wspawnvp** ( **_P_WAIT** określona dla *trybu*) jest stanem wyjścia nowego procesu. Wartość zwracana z asynchronicznej **_spawnvp** lub **_wspawnvp** ( **_P_NOWAIT** lub **_P_NOWAITO** określona dla *trybu*) to dojście do procesu. Stan zakończenia to 0, jeśli proces został przerwany normalnie. Można ustawić stan zakończenia na wartość różną od zera, jeśli proces duplikowany używa w pełni niezerowego argumentu do wywołania procedury **wyjściowej** . Jeśli nowy proces nie ustawił jawnie stanu wyjścia pozytywnego, stan wyjścia pozytywnego wskazuje nietypowe wyjście z przerwaniem lub przerwaniem. Zwracana wartość-1 wskazuje błąd (nowy proces nie jest uruchomiony). W tym przypadku **errno** jest ustawiony na jedną z następujących wartości:

|||
|-|-|
| **E2BIG** | Lista argumentów przekracza 1024 bajtów. |
| **EINVAL** | argument *trybu* jest nieprawidłowy. |
| **ENOENT** | Nie znaleziono pliku lub ścieżki. |
| **ENOEXEC** | Określony plik nie jest wykonywalny lub ma nieprawidłowy format pliku wykonywalnego. |
| **ENOMEM** | Za mało dostępnej pamięci, aby wykonać nowy proces. |

Aby uzyskać więcej informacji na temat tych i innych kodów powrotu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda z tych funkcji tworzy nowy proces i wykonuje go oraz przekazuje tablicę wskaźników do argumentów wiersza polecenia i używa zmiennej środowiskowej **Path** , aby znaleźć plik do wykonania.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *cmdname* lub *argv* jest wskaźnikiem typu null lub jeśli *argv* wskazuje na wskaźnik o wartości null lub *argv*[0] jest pustym ciągiem, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EINVAL**i zwracają-1. Nie jest duplikowany żaden nowy proces.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_spawnvp**|\<stdio. h > lub \<Process. h >|
|**_wspawnvp**|\<stdio. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [_spawn, _Wspawn Functions](../../c-runtime-library/spawn-wspawn-functions.md).

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec, funkcje](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
