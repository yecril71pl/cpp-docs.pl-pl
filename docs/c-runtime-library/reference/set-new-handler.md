---
title: _set_new_handler
ms.date: 4/2/2020
api_name:
- _set_new_handler
- _o__set_new_handler
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_new_handler
- set_new_handler
helpviewer_keywords:
- _set_new_handler function
- set_new_handler function
- error handling
- transferring control to error handler
ms.assetid: 1d1781b6-5cf8-486a-b430-f365e0bb023f
ms.openlocfilehash: c3f1b9bd8bf2a4404e2239858e4c3c59b755bacd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332373"
---
# <a name="_set_new_handler"></a>_set_new_handler

Przenosi kontrolę do mechanizmu obsługi błędów, jeśli **nowy** operator nie może przydzielić pamięci.

## <a name="syntax"></a>Składnia

```cpp
_PNH _set_new_handler( _PNH pNewHandler );
```

### <a name="parameters"></a>Parametry

*pNewHandler (ręczny)*<br/>
Wskaźnik do funkcji obsługi pamięci dostarczonej przez aplikację. Argument 0 powoduje, że nowy program obsługi do usunięcia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do poprzedniej funkcji obsługi wyjątków zarejestrowanej przez **_set_new_handler**, dzięki czemu poprzednia funkcja może zostać przywrócona później. Jeśli nie ustawiono poprzedniej funkcji, wartość zwracana może służyć do przywracania domyślnego zachowania; ta wartość może być **NULL**.

## <a name="remarks"></a>Uwagi

Funkcja **_set_new_handler** języka C++ określa funkcję obsługi wyjątków, która zyskuje kontrolę, jeśli **nowy** operator nie może przydzielić pamięci. Jeśli **nowy** nie powiedzie się, system czasu wykonywania automatycznie wywołuje funkcję obsługi wyjątków, która została przekazana jako argument do **_set_new_handler**. **_PNH**, zdefiniowane w New.h, jest wskaźnikiem do funkcji, która zwraca typ **int** i przyjmuje argument typu **size_t**. Użyj **size_t,** aby określić ilość miejsca do przydzielenia.

Nie ma domyślnego programu obsługi.

**_set_new_handler** jest zasadniczo schemat wyrzucania elementów bezużytecznych. System wykonywania ponawia alokację za każdym razem, gdy funkcja zwraca wartość niezerową i kończy się niepowodzeniem, jeśli funkcja zwraca wartość 0.

Wystąpienie funkcji **_set_new_handler** w programie rejestruje funkcję obsługi wyjątków określoną na liście argumentów za pomocą systemu czasu wykonywania:

```cpp
// set_new_handler1.cpp
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

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

Można zapisać adres funkcji, który został ostatnio przekazany do funkcji **_set_new_handler** i przywrócić go później:

```cpp
   _PNH old_handler = _set_new_handler( my_handler );
   // Code that requires my_handler
   // . . .
   _set_new_handler( old_handler )
   // Code that requires old_handler
   // . . .
```

Funkcja [_set_new_mode](set-new-mode.md) C++ ustawia nowy tryb obsługi dla [malloc](malloc.md). Nowy tryb obsługi wskazuje, czy w przypadku awarii **malloc** ma wywołać nową procedurę obsługi zgodnie z **_set_new_handler**. Domyślnie **malloc** nie wywołać nową procedurę obsługi na niepowodzenie alokacji pamięci. Można zastąpić to domyślne zachowanie, tak aby, gdy **malloc** nie można przydzielić pamięci, **malloc** wywołuje nową procedurę obsługi w taki sam sposób, jak **nowy** operator robi, gdy nie powiedzie się z tego samego powodu. Aby zastąpić wartość domyślną, zadzwoń:

```cpp
_set_new_mode(1);
```

na początku programu lub link z Newmode.obj.

Jeśli zostanie podany `operator new` zdefiniowany przez użytkownika, nowe funkcje obsługi nie są automatycznie wywoływane w przypadku awarii.

Aby uzyskać więcej informacji, zobacz [nowe](../../cpp/new-operator-cpp.md) i [usuń](../../cpp/delete-operator-cpp.md) w *odwołaniu do języka języka C++*.

Istnieje jeden **_set_new_handler** obsługi dla wszystkich dynamicznie połączonych bibliotek DLL lub plików wykonywalnych; nawet jeśli wywołasz **_set_new_handler** program obsługi może zostać zastąpiony przez inny lub który zastępuje program obsługi ustawiony przez inną bibliotekę DLL lub plik wykonywalny.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_new_handler**|\<> new.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

W tym przykładzie, gdy alokacja nie powiedzie się, kontrola jest przenoszona do MyNewHandler. Argument przekazany do MyNewHandler jest liczba bajtów żądane. Wartość zwrócona z MyNewHandler jest flagą wskazującą, czy alokacja powinna zostać ponowiona: wartość niezerowa wskazuje, że alokacja powinna zostać ponowiona, a wartość zero wskazuje, że alokacja nie powiodła się.

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

## <a name="see-also"></a>Zobacz też

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[Wolna](free.md)<br/>
[realloc](realloc.md)<br/>
