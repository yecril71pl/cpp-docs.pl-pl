---
title: _set_new_handler
ms.date: 11/04/2016
apiname:
- _set_new_handler
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_new_handler
- set_new_handler
helpviewer_keywords:
- _set_new_handler function
- set_new_handler function
- error handling
- transferring control to error handler
ms.assetid: 1d1781b6-5cf8-486a-b430-f365e0bb023f
ms.openlocfilehash: bc7718503f59c69868a75cac9383286a548fc307
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640313"
---
# <a name="setnewhandler"></a>_set_new_handler

Przekazuje sterowanie do Twojej mechanizm obsługi błędów, jeśli **nowe** operator nie może przydzielić pamięci.

## <a name="syntax"></a>Składnia

```cpp
_PNH _set_new_handler( _PNH pNewHandler );
```

### <a name="parameters"></a>Parametry

*pNewHandler*<br/>
Wskaźnik do obsługi funkcji pamięci dostarczonej przez aplikację. Argument 0 powoduje, że nowy program obsługi ma zostać usunięty.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do poprzedniego wyjątku, które są zarejestrowane w wyniku funkcji obsługi **_set_new_handler**, dzięki czemu można później przywrócić poprzedniej funkcji. Jeśli żadna funkcja poprzedniej została ustawiona, wartość zwracana można przywrócić domyślne zachowanie; Ta wartość może być **NULL**.

## <a name="remarks"></a>Uwagi

C++ **_set_new_handler** funkcji określa funkcję obsługi wyjątków, który przejmie kontrolę, jeśli **nowe** operator nie może przydzielić pamięci. Jeśli **nowe** zakończy się niepowodzeniem, system środowiska wykonawczego automatycznie wywołuje funkcję obsługi wyjątków, który został przekazany jako argument do **_set_new_handler**. **_PNH**, zdefiniowane w New.h, jest wskaźnikiem do funkcji, która zwraca typ **int** i przyjmuje argument typu **size_t**. Użyj **size_t** Aby określić ilość miejsca do przydzielenia.

Nie ma żadnych domyślny program obsługi.

**_set_new_handler** jest zasadniczo schemat wyrzucania elementów bezużytecznych. System środowiska wykonawczego ponawia próbę alokacji każdorazowo, funkcja zwraca wartość różną od zera i kończy się niepowodzeniem, jeśli funkcja zwraca wartość 0.

Wystąpienia **_set_new_handler** funkcji w programie rejestruje funkcję obsługi wyjątków, określone na liście argumentów za pomocą środowiska wykonawczego systemu:

```cpp
// set_new_handler1.cpp
#include <new.h>

int handle_program_memory_depletion( size_t )
{
   // Your code
}

int main( void )
{
   _set_new_handler( handle_program_memory_depletion );
   int *pi = new int[BIG_NUMBER];
}
```

Możesz zapisać adresu funkcji, który został ostatnio przekazany do **_set_new_handler** funkcji i przywrócić go później:

```cpp
   _PNH old_handler = _set_new_handler( my_handler );
   // Code that requires my_handler
   // . . .
   _set_new_handler( old_handler )
   // Code that requires old_handler
   // . . .
```

C++ [_set_new_mode](set-new-mode.md) funkcja Ustawia nowy tryb obsługi dla [— funkcja malloc](malloc.md). Nowy tryb obsługi wskazuje, czy w przypadku awarii, **— funkcja malloc** ma wywoływać nową procedurę obsługi zgodnie z ustawieniem **_set_new_handler**. Domyślnie **— funkcja malloc** nie wywołuje nowej procedury obsługi awarii w celu przydzielenia pamięci. Można zastąpić to zachowanie domyślne tak, aby, gdy **— funkcja malloc** nie może przydzielić pamięci, **— funkcja malloc** wywoła nową procedurę obsługi w taki sam sposób **nowe** jest operator Jeśli jej nie powiedzie się z tego samego powodu. Aby zastąpić domyślne, wywołaj polecenie:

```cpp
_set_new_mode(1);
```

na wczesnym etapie program lub Połącz z Newmode.obj.

Jeśli zdefiniowane przez użytkownika `operator new` zostanie podana, nowe funkcje obsługi nie są automatycznie wywoływane w przypadku niepowodzenia.

Aby uzyskać więcej informacji, zobacz [nowe](../../cpp/new-operator-cpp.md) i [Usuń](../../cpp/delete-operator-cpp.md) w *C++ Language Reference*.

Istnieje jeden **_set_new_handler** Obsługa wszystkie połączone dynamicznie biblioteki DLL lub pliki wykonywalne; nawet wtedy, gdy wywołujesz **_set_new_handler** programu obsługi może być zastąpiona przez inną lub zastąpienia Program obsługi ustawione przez innej biblioteki DLL lub pliku wykonywalnego.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_new_handler**|\<new.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

W tym przykładzie gdy przydział nie powiedzie się, kontrola jest przekazywana do MyNewHandler. Argument przekazany do MyNewHandler jest to liczba bajtów. Wartość zwracana z MyNewHandler jest flagę wskazującą, czy należy wykonać ponownie alokacji: wartość różną od zera wskazuje, że zakończonego alokacji, a wartość zero wskazuje, że alokacji nie powiodła się.

```cpp
// crt_set_new_handler.cpp
// compile with: /c
#include <stdio.h>
#include <new.h>
#define BIG_NUMBER 0x1fffffff

int coalesced = 0;

int CoalesceHeap()
{
   coalesced = 1;  // Flag RecurseAlloc to stop
   // do some work to free memory
   return 0;
}
// Define a function to be called if new fails to allocate memory.
int MyNewHandler( size_t size )
{
   printf("Allocation failed. Coalescing heap.\n");

   // Call a function to recover some heap space.
   return CoalesceHeap();
}

int RecurseAlloc() {
   int *pi = new int[BIG_NUMBER];
   if (!coalesced)
      RecurseAlloc();
   return 0;
}

int main()
{
   // Set the failure handler for new to be MyNewHandler.
   _set_new_handler( MyNewHandler );
   RecurseAlloc();
}
```

```Output
Allocation failed. Coalescing heap.

This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
