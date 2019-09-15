---
title: _set_new_handler
ms.date: 11/04/2016
api_name:
- _set_new_handler
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
ms.openlocfilehash: a1f340887efd657dd9ff9bf219534d77fdd90aa3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948469"
---
# <a name="_set_new_handler"></a>_set_new_handler

Przenosi kontrolę do mechanizmu obsługi błędów, jeśli **Nowy** operator nie może przydzielić pamięci.

## <a name="syntax"></a>Składnia

```cpp
_PNH _set_new_handler( _PNH pNewHandler );
```

### <a name="parameters"></a>Parametry

*pNewHandler*<br/>
Wskaźnik do funkcji obsługi pamięci dostarczonej przez aplikację. Argument 0 powoduje usunięcie nowej procedury obsługi.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do poprzedniej funkcji obsługi wyjątków zarejestrowanej przez **_set_new_handler**, aby można było przywrócić poprzednią funkcję. Jeśli żadna Poprzednia funkcja nie została ustawiona, wartość zwracana może zostać użyta do przywrócenia zachowania domyślnego. Ta wartość może być **równa null**.

## <a name="remarks"></a>Uwagi

C++ Funkcja **_set_new_handler** określa funkcję obsługi wyjątków, która uzyskuje kontrolę w przypadku niepowodzenia alokacji pamięci przez operatora **New** . Jeśli **nowe** nie powiodło się, system czasu wykonywania automatycznie wywoła funkcję obsługi wyjątków, która została przeniesiona jako argument do **_set_new_handler**. **_PNH**, zdefiniowany w New. h, jest wskaźnikiem do funkcji, która zwraca typ **int** i przyjmuje argument typu **size_t**. Użyj **size_t** , aby określić ilość miejsca do przydzielenia.

Brak domyślnej procedury obsługi.

**_set_new_handler** jest zasadniczo schematem odzyskiwania pamięci. System czasu wykonywania ponawia próbę przydzielania za każdym razem, gdy funkcja zwraca wartość różną od zera i kończy się niepowodzeniem, jeśli funkcja zwraca 0.

Wystąpienie funkcji **_set_new_handler** w programie rejestruje funkcję obsługi wyjątków określoną na liście argumentów z systemem w czasie wykonywania:

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

Można zapisać adres funkcji, który został ostatnio przekazano do funkcji **_set_new_handler** i przywrócić go później:

```cpp
   _PNH old_handler = _set_new_handler( my_handler );
   // Code that requires my_handler
   // . . .
   _set_new_handler( old_handler )
   // Code that requires old_handler
   // . . .
```

C++ Funkcja [_set_new_mode](set-new-mode.md) ustawia nowy tryb obsługi dla opcji [malloc](malloc.md). Nowy tryb obsługi wskazuje, czy w przypadku niepowodzenia, **malloc** ma wywołać nową procedurę obsługi jako ustawioną przez **_set_new_handler**. Domyślnie funkcja **malloc** nie wywołuje nowej procedury obsługi w przypadku niepowodzenia przydzielenia pamięci. Można zastąpić to zachowanie domyślne, tak aby w przypadku niepowodzenia przydzielenia pamięci przez funkcję **malloc** wywołuje nową procedurę obsługi w taki sam **sposób, w** jaki operator **New** wykonuje, gdy nie powiedzie się z tego samego powodu. Aby zastąpić wartość domyślną, należy wywołać:

```cpp
_set_new_mode(1);
```

Wczesne w programie lub Połącz z NewMode. obj.

Jeśli zostanie podany zdefiniowany `operator new` przez użytkownika, nowe funkcje obsługi nie są automatycznie wywoływane w przypadku niepowodzenia.

Aby uzyskać więcej informacji, zobacz [Nowość](../../cpp/new-operator-cpp.md) i [delete](../../cpp/delete-operator-cpp.md) w  *C++ dokumentacji języka*.

Istnieje jedna procedura obsługi **_set_new_handler** dla wszystkich dynamicznie połączonych bibliotek DLL lub plików wykonywalnych; nawet jeśli wywołasz **_set_new_handler** , program obsługi może zostać zastąpiony przez inny lub zastępujący procedurę obsługi ustawioną przez inną bibliotekę DLL lub plik wykonywalny.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_new_handler**|\<new.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

W tym przykładzie, gdy alokacja nie powiedzie się, formant jest transferowany do MyNewHandler. Argument przesłany do MyNewHandler jest liczbą żądanych bajtów. Wartość zwrócona przez MyNewHandler to Flaga wskazująca, czy należy ponowić próbę alokacji: wartość niezerowa wskazuje, że alokacja powinna zostać ponowiona, a wartość zerowa wskazuje, że alokacja nie powiodła się.

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
