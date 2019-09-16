---
title: _cwait
ms.date: 11/04/2016
api_name:
- _cwait
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
- _cwait
helpviewer_keywords:
- cwait function
- _cwait function
ms.assetid: d9b596b5-45f4-4e03-9896-3f383cb922b8
ms.openlocfilehash: b4be342ef528959bae22917bc59eef5a953aa4ae
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937749"
---
# <a name="_cwait"></a>_cwait

Czeka, aż inny proces zakończy działanie.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Wskaźnik do buforu, w którym będzie przechowywany kod wyniku określonego procesu, lub **wartość null**.

*procHandle*<br/>
Dojście do procesu, w którym ma się oczekiwać (czyli proces, który musi zakończyć się, zanim **_cwait** może zwrócić).

*transakcji*<br/>
WARTOŚĆ NULL: Ignorowane przez aplikacje systemu operacyjnego Windows; w przypadku innych aplikacji: kod akcji do wykonania na *procHandle*.

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym zakończeniu określonego procesu program zwraca dojście określonego procesu i ustawia *termstat* na kod wyniku, który jest zwracany przez określony proces. W przeciwnym razie zwraca-1 i ustawia **errno** w następujący sposób.

|Wartość|Opis|
|-----------|-----------------|
|**ECHILD**|Nie istnieje określony proces, *procHandle* jest nieprawidłowy lub wywołanie interfejsu API [GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess) lub [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject) nie powiodło się.|
|**EINVAL**|*Akcja* jest nieprawidłowa.|

Aby uzyskać więcej informacji na temat tych i innych kodów powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_cwait** czeka na zakończenie procesu o identyfikatorze określonego przez *procHandle*. Wartość *procHandle* , która jest przesyłana do **_cwait** powinna być wartością zwracaną przez wywołanie funkcji [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) , która utworzyła określony proces. Jeśli identyfikator procesu kończy się przed wywołaniem **_cwait** , **_cwait** zwraca natychmiast. **_cwait** może być używana przez każdy proces do oczekiwania na każdy inny znany proces, dla którego istnieje prawidłowe dojście (*procHandle*).

*termstat* wskazuje bufor, w którym będzie przechowywany kod powrotny określonego procesu. Wartość *termstat* wskazuje, czy określony proces został przerwany normalnie przez wywołanie interfejsu API [ExitProcess —](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) systemu Windows. **ExitProcess —** jest wywoływana wewnętrznie, jeśli określony proces wywołuje metodę **Exit** lub **_exit**, zwraca z elementu **Main**lub osiągnie koniec elementu **głównego**. Aby uzyskać więcej informacji na temat wartości, która jest przenoszona z powrotem za pomocą *termstat*, zobacz [GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess). Jeśli **_cwait** jest wywoływana przy użyciu wartości **null** dla *termstat*, kod powrotny określonego procesu nie jest przechowywany.

Parametr *Action* jest ignorowany przez system operacyjny Windows, ponieważ relacje nadrzędny-podrzędny nie są zaimplementowane w tych środowiskach.

Jeśli *procHandle* ma wartość-1 lub-2 (uchwyty do bieżącego procesu lub wątku), uchwyt zostanie zamknięty. W związku z tym w tej sytuacji nie należy używać zwracanego uchwytu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_cwait**|\<process.h>|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, _wspawn, funkcje](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
