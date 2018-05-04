---
title: set_unexpected — (CRT) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- set_unexpected
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
apitype: DLLExport
f1_keywords:
- set_unexpected
dev_langs:
- C++
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a0c97f46a66a26f107061676dba313b068e9aebf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="setunexpected-crt"></a>set_unexpected (CRT)

Instaluje własnej funkcji zakończenia ma zostać wywołana przez **nieoczekiwany**.

## <a name="syntax"></a>Składnia

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>Parametry

*unexpFunction*<br/>
Wskaźnik do funkcji, która zapisu zastąpić **nieoczekiwany** funkcji.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do funkcji zakończenia poprzedniej zarejestrowany przez **_set_unexpected** tak, aby później można przywrócić poprzedniego funkcji. Jeśli nie ustawiono Brak poprzedniej funkcji, zwracana wartość może służyć do przywrócić domyślne zachowanie; Ta wartość może mieć wartości NULL.

## <a name="remarks"></a>Uwagi

**Set_unexpected —** funkcji instaluje *unexpFunction* jako funkcja wywoływana przez **nieoczekiwany**. **Nieoczekiwany** nie jest używana w bieżącej implementacji obsługi wyjątków C++. **Unexpected_function** typ jest zdefiniowany w EH. H jako wskaźnik do zdefiniowanych przez użytkownika funkcji nieoczekiwany, *unexpFunction* zwracającą **void**. Niestandardowe *unexpFunction* funkcja nie może zwracać do swojego obiektu wywołującego.

```cpp
typedef void ( *unexpected_function )( );
```

Domyślnie **nieoczekiwany** wywołania **przerwanie**. To zachowanie domyślne można zmienić, pisanie funkcji zakończenia i wywołanie **set_unexpected —** z nazwą funkcji jako jej argument. **Nieoczekiwany** wywołuje ostatniej podany jako argument do funkcji **set_unexpected —**.

W odróżnieniu od funkcji niestandardowych zakończenia zainstalowane przez wywołanie do **set_terminate —**, może zostać wygenerowany wyjątek z poziomu *unexpFunction*.

W środowisku wielowątkowym nieoczekiwany funkcje są obsługiwane osobno dla każdego wątku. Każdym nowym wątku, należy zainstalować nieoczekiwany funkcji. W związku z tym każdy wątek jest odpowiedzialny za własną nieoczekiwany obsługi.

Bieżący implementacji Microsoft C++, obsługa wyjątków **nieoczekiwany** wywołania **przerwanie** domyślnie i nigdy nie jest wywoływany przez biblioteki wykonawczej obsługi wyjątków. Nie ma żadnych dodatkowych zalet określonego wywołania **nieoczekiwany** zamiast **przerwanie**.

Istnieje jeden **set_unexpected —** obsługę wszystkie połączone dynamicznie biblioteki DLL lub exe; nawet wtedy, gdy jest wywoływana **set_unexpected —** programu obsługi może być zastąpiony innym lub zamienianych ustawione przez program obsługi innego pliku DLL lub EXE.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**set_unexpected**|\<eh.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków — procedury](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_unexpected](get-unexpected.md)<br/>
[set_terminate —](set-terminate-crt.md)<br/>
[Zakończenie](terminate-crt.md)<br/>
[Nieoczekiwany](unexpected-crt.md)<br/>
