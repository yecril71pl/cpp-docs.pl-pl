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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 08ea5bb8c446fadac6a7bcf7ca172c5d14546776
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332103"
---
# <a name="set_terminate-crt"></a>set_terminate (CRT)

Instaluje własną procedurę zakończenia, która ma być wywoływana przez **zakończenie**.

## <a name="syntax"></a>Składnia

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>Parametry

*termFunction (Funkcja termFunction)*<br/>
Wskaźnik do funkcji zakończenia, którą piszesz.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do poprzedniej funkcji zarejestrowanej przez **set_terminate,** dzięki czemu poprzednia funkcja może zostać przywrócona później. Jeśli nie ustawiono poprzedniej funkcji, wartość zwracana może służyć do przywracania domyślnego zachowania; wartość ta może być **null**.

## <a name="remarks"></a>Uwagi

Funkcja **set_terminate** instaluje *termFunction* jako funkcję wywołaną przez **zakończenie**. **set_terminate** jest używany z obsługą wyjątków C++ i może być wywoływana w dowolnym momencie w programie przed odrzuceniem wyjątku. **domyślnie kończyć** [połączenia przerywać.](abort.md) Tę wartość domyślną można zmienić, pisząc własną funkcję zakończenia i wywołując **set_terminate** z nazwą funkcji jako argumentem. **zakończyć** wywołuje ostatnią funkcję podana jako argument do **set_terminate**. Po wykonaniu dowolnych pożądanych zadań *oczyszczania, termFunction* powinien zakończyć program. Jeśli nie zakończy (jeśli powróci do swojego wywołującego), [przerwania](abort.md) jest wywoływana.

W środowisku wielowątkowym funkcje zakończenia są obsługiwane oddzielnie dla każdego wątku. Każdy nowy wątek musi zainstalować własną funkcję zakończenia. W związku z tym każdy wątek jest odpowiedzialny za własną obsługę zakończenia.

Typ **terminate_function** jest zdefiniowany w EH. H jako wskaźnik do zdefiniowanej przez użytkownika funkcji *zakończenia, termFunction,* która zwraca **void**. Funkcja niestandardowa *termFunction* może przyjmować żadnych argumentów i nie powinien powrócić do jego wywołującego. Jeśli tak, [przerwania](abort.md) jest wywoływana. Wyjątek nie może być zgłaszany z wewnątrz *termFunction*.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> Funkcja **set_terminate** działa tylko poza debugerem.

Istnieje jeden **program** obsługi set_terminate dla wszystkich dynamicznie połączonych bibliotek DLL lub EXE; nawet jeśli wywołasz **set_terminate** program obsługi może zostać zastąpiony przez inny lub może być zastąpienie programu obsługi ustawionego przez inną bibliotekę DLL lub EXE.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**set_terminate**|\<eh.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [zakończenia](terminate-crt.md).

## <a name="see-also"></a>Zobacz też

[Procedury obsługi wyjątków](../../c-runtime-library/exception-handling-routines.md)<br/>
[Przerwać](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[Zakończyć](terminate-crt.md)<br/>
[Nieoczekiwane](unexpected-crt.md)<br/>
