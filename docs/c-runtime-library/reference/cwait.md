---
title: _cwait
ms.date: 11/04/2016
apiname:
- _cwait
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
- api-ms-win-crt-process-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _cwait
helpviewer_keywords:
- cwait function
- _cwait function
ms.assetid: d9b596b5-45f4-4e03-9896-3f383cb922b8
ms.openlocfilehash: f7a49497ac71ec15261e1215bd2bbed2e49f42ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50489625"
---
# <a name="cwait"></a>_cwait

Czeka, aż do zakończenia inny proces.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Wskaźnik do buforu, w którym będą przechowywane kod wyniku określonego procesu, lub **NULL**.

*procHandle*<br/>
Dojście do procesu oczekiwania (oznacza to, że proces, który ma zostać przerwany przed **_cwait** może zwrócić).

*Akcja*<br/>
Wartość NULL: Ignorowane przez aplikacje systemu operacyjnego Windows; w przypadku innych aplikacji: kod akcji do wykonania na *procHandle*.

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym ukończeniu określonego procesu zwraca uchwyt określony proces i ustawia *termstat* na kod rezultatu, który jest zwracany przez określonego procesu. W przeciwnym razie zwraca wartość -1 i ustawia **errno** w następujący sposób.

|Wartość|Opis|
|-----------|-----------------|
|**ECHILD**|Nie istnieje żaden określony proces, *procHandle* jest nieprawidłowy lub wywołanie [GetExitCodeProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess) lub [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) interfejsu API nie powiodło się.|
|**EINVAL**|*Akcja* jest nieprawidłowy.|

Aby uzyskać więcej informacji na temat tych i innych kodach powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Cwait** funkcja czeka na zakończenie procesu o identyfikatorze określonego procesu dostarczonego przez *procHandle*. Wartość *procHandle* przekazana do **_cwait** powinien mieć wartość, który jest zwracany przez wywołanie metody [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) funkcja, która utworzyła określonego procesu. Jeśli identyfikator procesu zakończy się przed **_cwait** jest wywoływana, **_cwait** zwraca natychmiast. **_cwait** może służyć przez żaden proces zaczekać jakiś inny proces znany, dla którego prawidłowego uchwytu (*procHandle*) istnieje.

*termstat* wskazuje buforu, w którym będą przechowywane kod powrotny określonego procesu. Wartość *termstat* wskazuje, czy określony proces zakończył się normalnie, wywołując Windows [exitprocess —](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-exitprocess) interfejsu API. **Exitprocess —** jest wywoływana wewnętrznie, jeśli określony proces wywołuje **wyjść** lub **_exit**, zwraca z **głównego**, lub dociera do końca **głównego** . Aby uzyskać więcej informacji o wartości, który jest przekazywany za pośrednictwem *termstat*, zobacz [GetExitCodeProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess). Jeśli **_cwait** jest wywoływana za pomocą **NULL** wartość *termstat*, nie znajduje się kod powrotny określonego procesu.

*Akcji* parametru jest ignorowana przez system operacyjny Windows, ponieważ relacji nadrzędny podrzędny nie są implementowane w tych środowiskach.

Chyba że *procHandle* jest wartość -1 lub -2 (obsługiwane bieżący proces lub wątek), uchwyt zostanie zamknięte. W związku z tym w takiej sytuacji nie należy używać zwracany uchwyt.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_cwait**|\<process.h >|\<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
