---
title: _cwait — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- cwait function
- _cwait function
ms.assetid: d9b596b5-45f4-4e03-9896-3f383cb922b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 878c1c08dabe52a31a2bdf377c3e0bb167a9ae5d
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450951"
---
# <a name="cwait"></a>_cwait

Oczekuje, aż inny proces zakończy się.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Wskaźnik do buforu, na którym będzie przechowywany kod wyniku określonego procesu, lub **NULL**.

*procHandle*<br/>
Dojście oczekiwania proces (oznacza to, że proces, który ma zostać przerwany przed **_cwait —** może zwrócić).

*Akcja*<br/>
Wartość NULL: Ignorowane w aplikacjach systemu operacyjnego Windows; w przypadku innych aplikacji: kod akcji do wykonania na *procHandle*.

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym ukończeniu określony proces Zwraca dojście określony proces i ustawia *termstat* kod wynik zwracany przez określony proces. W przeciwnym razie zwraca wartość -1 i ustawia **errno** w następujący sposób.

|Wartość|Opis|
|-----------|-----------------|
|**ECHILD —**|Nie istnieje żaden określony proces, *procHandle* jest nieprawidłowy lub wywołanie [GetExitCodeProcess](http://msdn.microsoft.com/library/windows/desktop/ms683189.aspx) lub [WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032.aspx) interfejsu API nie powiodło się.|
|**EINVAL —**|*Akcja* jest nieprawidłowy.|

Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Cwait —** funkcja czeka na zakończenie procesu identyfikator określony proces zapewnianej przez *procHandle*. Wartość *procHandle* przekazywany do **_cwait —** powinna być wartością zwracaną przez wywołanie [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) funkcja, która utworzyła określony proces. Jeśli identyfikator procesu kończy się przed **_cwait —** jest nazywany **_cwait —** natychmiast kończy pracę. **_cwait —** pozwala przez żaden proces, poczekaj, aż inny proces znany dla którego prawidłowego dojścia (*procHandle*) istnieje.

*termstat* wskazuje buforu, na którym będzie przechowywany kod powrotny określony proces. Wartość *termstat* wskazuje, czy określony proces został przerwany zwykle przez wywołanie systemu Windows [ExitProcess](http://msdn.microsoft.com/library/windows/desktop/ms682658.aspx) interfejsu API. **ExitProcess** jest wywoływana wewnętrznie, gdy określony proces wywołuje **zakończyć** lub **_exit —**, zwraca z **głównego**, lub dociera do końca **głównego** . Aby uzyskać więcej informacji o wartość, która jest przekazywany z powrotem przy użyciu *termstat*, zobacz [GetExitCodeProcess](http://msdn.microsoft.com/library/windows/desktop/ms683189.aspx). Jeśli **_cwait —** jest wywoływana przy użyciu **NULL** wartość *termstat*, nie znajduje się kod powrotny określonego procesu.

*Akcji* parametru jest ignorowana przez system operacyjny Windows, ponieważ relacji nadrzędny podrzędny nie są zaimplementowane w tych środowiskach.

O ile *procHandle* jest wartość -1 lub -2 (obsługiwane bieżący proces lub wątek), dojście zostanie zamknięte. W związku z tym w takiej sytuacji nie należy używać zwrócony dojścia.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_cwait**|\<process.h >|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
