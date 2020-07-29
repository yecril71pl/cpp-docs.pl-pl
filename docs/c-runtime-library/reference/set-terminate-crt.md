---
title: set_terminate (CRT)
ms.date: 4/2/2020
api_name:
- set_terminate
- _o_set_terminate
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_terminate
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
ms.openlocfilehash: 70ed4adb7ceada53205fd69f111c8976fe95c711
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234019"
---
# <a name="set_terminate-crt"></a>set_terminate (CRT)

Instaluje własną procedurę zakończenia, która ma zostać wywołana przez **zakończenie**.

## <a name="syntax"></a>Składnia

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>Parametry

*termFunction*<br/>
Wskaźnik do funkcji kończenia, którą napiszesz.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do poprzedniej funkcji zarejestrowanej przez **set_terminate** , aby można było przywrócić poprzednią funkcję. Jeśli nie ustawiono poprzedniej funkcji, wartość zwracana może zostać użyta do przywrócenia zachowania domyślnego. Ta wartość może być **równa null**.

## <a name="remarks"></a>Uwagi

Funkcja **set_terminate** instaluje *termFunction* jako funkcję wywołana przez **zakończenie**. **set_terminate** jest używany z obsługą wyjątków C++ i może być wywoływana w dowolnym momencie w programie przed zgłoszeniem wyjątku. **przerywaj wywołania domyślnie** . [abort](abort.md) Można zmienić to ustawienie domyślne, pisząc własną funkcję zakończenia i wywołując **set_terminate** z nazwą funkcji jako argumentem. **Przerwij** wywołuje ostatnią funkcję podaną jako argument do **set_terminate**. Po wykonaniu wszystkich żądanych zadań oczyszczania *termFunction* powinien wyjść z programu. Jeśli nie zakończy się (jeśli powróci do jego obiektu wywołującego), wywoływana jest metoda [Abort](abort.md) .

W środowisku wielowątkowym funkcje Przerwij są obsługiwane oddzielnie dla każdego wątku. Każdy nowy wątek musi zainstalować własną funkcję terminate. W ten sposób każdy wątek jest odpowiedzialny za jego własną zakończenie obsługi.

Typ **terminate_function** jest zdefiniowany w EH. H jako wskaźnik do funkcji zakończenia zdefiniowanej przez użytkownika, *termFunction* , która zwraca wartość **`void`** . Funkcja niestandardowa *termFunction* może nie przyjmować argumentów i nie powinna zwracać do obiektu wywołującego. W takim przypadku wywoływana jest metoda [Abort](abort.md) . Wyjątek nie może zostać zgłoszony z poziomu *termFunction*.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> Funkcja **set_terminate** działa tylko poza debugerem.

Istnieje jedna procedura obsługi **set_terminate** dla wszystkich dynamicznie połączonych bibliotek DLL lub exe; nawet w przypadku wywołania **set_terminate** program obsługi może zostać zastąpiony przez inny element lub zamienić procedurę obsługi ustawioną przez inną bibliotekę DLL lub exe.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**set_terminate**|\<eh.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [przerwania](terminate-crt.md).

## <a name="see-also"></a>Zobacz także

[Procedury obsługi wyjątków](../../c-runtime-library/exception-handling-routines.md)<br/>
[przerwij](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[kończyć](terminate-crt.md)<br/>
[oczekiwan](unexpected-crt.md)<br/>
