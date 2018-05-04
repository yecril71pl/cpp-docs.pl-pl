---
title: set_terminate — (CRT) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- set_terminate
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
- set_terminate
dev_langs:
- C++
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 017ea9d96cef9065ff82e7f3428e725b816c9319
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="setterminate-crt"></a>set_terminate (CRT)

Instaluje własnego procedury zakończenia ma zostać wywołana przez **przerwanie**.

## <a name="syntax"></a>Składnia

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>Parametry

*termFunction*<br/>
Wskaźnik do funkcji przerwania, który można zapisać.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do funkcji poprzednie zarejestrowane przez **set_terminate —** tak, aby później można przywrócić poprzedniego funkcji. Jeśli nie ustawiono Brak poprzedniej funkcji, zwracana wartość może służyć do przywrócić domyślne zachowanie; Ta wartość może mieć wartości NULL.

## <a name="remarks"></a>Uwagi

**Set_terminate —** funkcji instaluje *termFunction* jako funkcja wywoływana przez **przerwanie**. **set_terminate —** jest używany z C++, obsługa wyjątków i może być wywoływana w dowolnym momencie w programie przed wyjątku. **przerwanie** wywołania [przerwać](abort.md) domyślnie. To ustawienie domyślne można zmienić, pisanie funkcji zakończenia i wywołanie **set_terminate —** z nazwą funkcji jako jej argument. **przerwanie** wywołuje ostatniej podany jako argument do funkcji **set_terminate —**. Po wykonywania żądanego zadania oczyszczania *termFunction* powinno zakończyć program. Jeśli nie zostanie zamknięta (jeśli wraca do swojego obiektu wywołującego), [przerwać](abort.md) jest wywoływana.

W środowisku wielowątkowym, należy zakończyć funkcje są obsługiwane osobno dla każdego wątku. Każdym nowym wątku, należy zainstalować ma własną funkcję przerwania. W związku z tym każdy wątek jest odpowiedzialny za własną obsługi zakończenia.

**Terminate_function —** typ jest zdefiniowany w EH. H jako wskaźnik do funkcji zdefiniowanej przez użytkownika zakończenia *termFunction* zwracającą **void**. Niestandardowej funkcji *termFunction* może nie przyjmują argumentów i nie może zwracać do swojego obiektu wywołującego. Jeśli tak, [przerwać](abort.md) jest wywoływana. Wyjątek nie może zostać zgłoszony z poziomu *termFunction*.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> **Set_terminate —** funkcja działa tylko poza debugerem.

Istnieje jeden **set_terminate —** obsługę wszystkie połączone dynamicznie biblioteki DLL lub exe; nawet wtedy, gdy jest wywoływana **set_terminate —** programu obsługi może być zastąpiony innym lub może zastępowanie ustawiony przez inny program obsługi Biblioteki DLL lub EXE.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**set_terminate —**|\<eh.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [przerwanie](terminate-crt.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków — procedury](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[Zakończenie](terminate-crt.md)<br/>
[Nieoczekiwany](unexpected-crt.md)<br/>
