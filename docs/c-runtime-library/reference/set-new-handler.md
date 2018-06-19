---
title: _set_new_handler — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _set_new_handler function
- set_new_handler function
- error handling
- transferring control to error handler
ms.assetid: 1d1781b6-5cf8-486a-b430-f365e0bb023f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30cd0c2a991ec046b0b1f55100c58641833cb992
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409813"
---
# <a name="setnewhandler"></a>_set_new_handler

Przekazuje sterowanie z mechanizmu obsługi błędów, jeśli **nowe** operator nie może przydzielić pamięci.

## <a name="syntax"></a>Składnia

```cpp
_PNH _set_new_handler( _PNH pNewHandler );
```

### <a name="parameters"></a>Parametry

*pNewHandler*<br/>
Wskaźnik do obsługi funkcji pamięci dostarczone przez aplikację. Argumentu o wartości 0 spowoduje, że nowy program obsługi ma zostać usunięty.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do poprzedniego wyjątku obsługi zarejestrowany przez funkcję **_set_new_handler —**, tak aby później można przywrócić poprzedniego funkcji. Jeśli nie ustawiono Brak poprzedniej funkcji, zwracana wartość można przywrócić domyślne zachowanie; Ta wartość może być **NULL**.

## <a name="remarks"></a>Uwagi

C++ **_set_new_handler —** funkcji określa funkcję obsługi wyjątków, który przejmuje kontrolę, jeśli **nowe** operator nie może przydzielić pamięci. Jeśli **nowe** kończy się niepowodzeniem, system środowiska wykonawczego automatycznie wywołuje funkcję obsługi wyjątków, który został przekazany jako argument **_set_new_handler —**. **_Pnh —**, zdefiniowane w New.h, wskaźnik do funkcji, która zwraca typ **int** i przyjmuje argument typu **size_t**. Użyj **size_t** do określenia ilości miejsca do przydzielenia.

Nie ma żadnych domyślny program obsługi.

**_set_new_handler —** jest zasadniczo schemat wyrzucanie elementów bezużytecznych. System środowiska wykonawczego ponowi próbę alokacji każdorazowo, funkcja zwraca wartość różną od zera i kończy się niepowodzeniem, jeśli funkcja zwraca wartość 0.

Wystąpienia **_set_new_handler —** funkcji w programie rejestruje określone na liście argumentów w systemie czasu wykonywania funkcji obsługi wyjątków:

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

Możesz zapisać adresu funkcji, który ostatnio został przekazany do **_set_new_handler —** działać, a później przywrócić:

```cpp
   _PNH old_handler = _set_new_handler( my_handler );
   // Code that requires my_handler
   // . . .
   _set_new_handler( old_handler )
   // Code that requires old_handler
   // . . .
```

C++ [_set_new_mode —](set-new-mode.md) funkcja ustawia tryb obsługi nowych [— funkcja malloc](malloc.md). Nowy tryb obsługi wskazuje, czy w przypadku awarii, **— funkcja malloc** jest wywołanie nowe procedury obsługi zgodnie z ustawieniami **_set_new_handler —**. Domyślnie **— funkcja malloc** nie wywołuje nowe procedury obsługi nie można przydzielić pamięci. Można zastąpić to zachowanie domyślne, aby, gdy **— funkcja malloc** nie może przydzielić pamięci, **— funkcja malloc** wywołuje nowe procedury obsługi w taki sam jak robi **nowe** operator jest Jeśli go nie powiodło się z tego samego powodu. Aby zastąpić domyślną, należy wywołać:

```cpp
_set_new_mode(1);
```

na początku program lub Połącz z biblioteką Newmode.obj.

Jeśli zdefiniowane przez użytkownika `operator new` została podana, nowe funkcje programu obsługi nie są automatycznie wywoływać w przypadku awarii.

Aby uzyskać więcej informacji, zobacz [nowe](../../cpp/new-operator-cpp.md) i [usunąć](../../cpp/delete-operator-cpp.md) w *dokumentacja języka C++*.

Istnieje jeden **_set_new_handler —** obsługę wszystkie połączone dynamicznie biblioteki DLL lub pliki wykonywalne; nawet wtedy, gdy jest wywoływana **_set_new_handler —** Twojego programu obsługi może zostać zastąpione przez inny lub użytkownik zastępuje Program obsługi ustawione przez innego pliku DLL lub wykonywalnego.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_new_handler**|\<new.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

W tym przykładzie przypadku alokacja nie powiedzie się, sterowanie jest przekazywane na MyNewHandler. Argument przekazany do MyNewHandler jest to liczba bajtów. Flaga wskazująca, czy należy wykonać ponownie alokacji jest wartość zwracana z MyNewHandler: wartość niezerowa wskazuje, że należy wykonać ponownie alokacji i wartość zerowa wskazuje na to, że nie ma alokacji.

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
