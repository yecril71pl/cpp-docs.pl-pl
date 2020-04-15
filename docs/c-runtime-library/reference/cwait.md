---
title: _cwait
ms.date: 4/2/2020
api_name:
- _cwait
- _o__cwait
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cwait
helpviewer_keywords:
- cwait function
- _cwait function
ms.assetid: d9b596b5-45f4-4e03-9896-3f383cb922b8
ms.openlocfilehash: d54f62c8ce391b2c8ead92a0a73ac48e6f2b3cb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348148"
---
# <a name="_cwait"></a>_cwait

Czeka, aż zakończy się kolejny proces.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
intptr_t _cwait(
   int *termstat,
   intptr_t procHandle,
   int action
);
```

### <a name="parameters"></a>Parametry

*termstat*<br/>
Wskaźnik do buforu, w którym będzie przechowywany kod wyniku określonego procesu, lub **NULL**.

*procHandle (procHandle)*<br/>
Dojście do procesu, aby poczekać na (oznacza to, że proces, który musi zakończyć się przed **_cwait** może zwrócić).

*Działania*<br/>
NULL: Ignorowane przez aplikacje systemu operacyjnego Windows; dla innych aplikacji: kod akcji do wykonania na *procHandle*.

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym zakończeniu określonego procesu zwraca dojście określonego procesu i ustawia *termstat* do kodu wynikowego, który jest zwracany przez określony proces. W przeciwnym razie zwraca wartość -1 i ustawia **errno** w następujący sposób.

|Wartość|Opis|
|-----------|-----------------|
|**ECHILD (ECHILD)**|Nie istnieje określony proces, *procHandle* jest nieprawidłowy lub wywołanie [getexitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess) lub [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject) API nie powiodło się.|
|**Einval**|*jest* nieprawidłowa.|

Aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_cwait** czeka na zakończenie identyfikatora procesu określonego procesu, który jest dostarczany przez *procHandle*. Wartość *procHandle,* który jest przekazywany do **_cwait** powinna być wartość, która jest zwracana przez wywołanie [funkcji _spawn,](../../c-runtime-library/spawn-wspawn-functions.md) który utworzył określony proces. Jeśli identyfikator procesu kończy się przed **wywołaniem _cwait,** **_cwait** zwraca natychmiast. **_cwait** może być używany przez dowolny proces, aby czekać na inny znany proces, dla którego istnieje prawidłowy dojście (*procHandle).*

*termstat* wskazuje bufor, w którym będzie przechowywany kod zwrotny określonego procesu. Wartość *termstat* wskazuje, czy określony proces zakończył się normalnie przez wywołanie interfejsu API [Windows ExitProcess.](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) **ExitProcess** jest wywoływana wewnętrznie, jeśli określony proces wywołuje **exit** lub **_exit**, zwraca z **głównego**lub osiągnie koniec **głównego**. Aby uzyskać więcej informacji na temat wartości przekazywanej z powrotem przez *termstat*, zobacz [GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess). Jeśli **_cwait** jest wywoływana przy użyciu wartości **NULL** dla *termstat,* kod zwrotny określonego procesu nie jest przechowywany.

Parametr *akcji* jest ignorowany przez system operacyjny Windows, ponieważ relacje nadrzędny-podrzędny nie są implementowane w tych środowiskach.

Chyba że *procHandle* jest -1 lub -2 (uchwyty do bieżącego procesu lub wątku), dojście zostanie zamknięty. W związku z tym w tej sytuacji nie należy używać zwracany dojście.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_cwait**|\<> proces.h|\<> errno.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_cwait.c
// compile with: /c
// This program launches several processes and waits
// for a specified process to finish.

#define _CRT_RAND_S

#include <windows.h>
#include <process.h>
#include <stdlib.h>
#include <stdio.h>
#include <time.h>

// Macro to get a random integer within a specified range
#define getrandom( min, max ) (( (rand_s (&number), number) % (int)((( max ) + 1 ) - ( min ))) + ( min ))

struct PROCESS
{
   int     nPid;
   char    name[40];
} process[4] = { { 0, "Ann" }, { 0, "Beth" }, { 0, "Carl" }, { 0, "Dave" } };

int main( int argc, char *argv[] )
{
   int termstat, c;
   unsigned int number;

   srand( (unsigned)time( NULL ) );    // Seed randomizer

   // If no arguments, this is the calling process
   if ( argc == 1 )
   {
      // Spawn processes in numeric order
      for ( c = 0; c < 4; c++ ) {
         _flushall();
         process[c].nPid = _spawnl( _P_NOWAIT, argv[0], argv[0],
                                    process[c].name, NULL );
      }

      // Wait for randomly specified process, and respond when done
      c = getrandom( 0, 3 );
      printf( "Come here, %s.\n", process[c].name );
      _cwait( &termstat, process[c].nPid, _WAIT_CHILD );
      printf( "Thank you, %s.\n", process[c].name );

   }
   // If there are arguments, this must be a spawned process
   else
   {
      // Delay for a period that's determined by process number
      Sleep( (argv[1][0] - 'A' + 1) * 1000L );
      printf( "Hi, Dad. It's %s.\n", argv[1] );
   }
}
```

```Output
Hi, Dad. It's Ann.
Come here, Ann.
Thank you, Ann.
Hi, Dad. It's Beth.
Hi, Dad. It's Carl.
Hi, Dad. It's Dave.
```

## <a name="see-also"></a>Zobacz też

[Kontrola procesu i środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
