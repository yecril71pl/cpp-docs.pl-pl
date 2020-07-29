---
title: set_unexpected (CRT)
ms.date: 11/04/2016
api_name:
- set_unexpected
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_unexpected
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
ms.openlocfilehash: f05eab14a53c8abc119a8014d5ac99dc076a9c25
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226167"
---
# <a name="set_unexpected-crt"></a>set_unexpected (CRT)

Instaluje własną funkcję zakończenia, która ma zostać wywołana przez **nieoczekiwane**.

## <a name="syntax"></a>Składnia

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>Parametry

*unexpFunction*<br/>
Wskaźnik do funkcji, którą napiszesz, aby zastąpić **nieoczekiwaną** funkcję.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do poprzedniej funkcji zakończenia zarejestrowanej przez **_set_unexpected** , aby można było przywrócić poprzednią funkcję. Jeśli nie ustawiono poprzedniej funkcji, wartość zwracana może zostać użyta do przywrócenia zachowania domyślnego. Ta wartość może być **równa null**.

## <a name="remarks"></a>Uwagi

Funkcja **set_unexpected** instaluje *unexpFunction* jako funkcję wywołana przez **nieoczekiwaną**. **nieoczekiwany** nie jest używany w bieżącej implementacji obsługi wyjątków C++. Typ **unexpected_function** jest zdefiniowany w EH. H jako wskaźnik do nieoczekiwanej funkcji zdefiniowanej przez użytkownika, *unexpFunction* , która zwraca wartość **`void`** . Niestandardowa funkcja *unexpFunction* nie powinna zwracać do obiektu wywołującego.

```cpp
typedef void ( *unexpected_function )( );
```

Domyślnie **nieoczekiwane** wywołania **kończą**. To zachowanie domyślne można zmienić, pisząc własną funkcję zakończenia i wywołując **set_unexpected** z nazwą funkcji jako argumentem. **nieoczekiwane** wywołania ostatnią funkcję podaną jako argument **set_unexpected**.

W przeciwieństwie do niestandardowej funkcji zakończenia zainstalowanej przez wywołanie do **set_terminate**, wyjątek może być zgłaszany z poziomu *unexpFunction*.

W środowisku wielowątkowym nieoczekiwane funkcje są obsługiwane osobno dla każdego wątku. Każdy nowy wątek musi zainstalować własną nieoczekiwaną funkcję. W ten sposób każdy wątek jest odpowiedzialny za jego własną nieoczekiwaną obsługę.

W bieżącej implementacji obsługi wyjątków języka C++, **nieoczekiwane** wywołania **kończą** się domyślnie i nigdy nie są wywoływane przez bibliotekę wykonawczą obsługującą wyjątek. Nie ma konkretnej możliwości wywoływania **nieoczekiwanego** , a nie **przerwania**.

Istnieje jedna procedura obsługi **set_unexpected** dla wszystkich dynamicznie połączonych bibliotek DLL lub exe; nawet w przypadku wywołania **set_unexpected** program obsługi może być zastępowany przez inny lub zastępujący moduł obsługi ustawiony przez inną bibliotekę DLL lub exe.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**set_unexpected**|\<eh.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Procedury obsługi wyjątków](../../c-runtime-library/exception-handling-routines.md)<br/>
[przerwij](abort.md)<br/>
[_get_unexpected](get-unexpected.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[kończyć](terminate-crt.md)<br/>
[oczekiwan](unexpected-crt.md)<br/>
