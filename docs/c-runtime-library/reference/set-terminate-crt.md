---
title: set_terminate (CRT)
ms.date: 11/04/2016
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
helpviewer_keywords:
- set_terminate function
- terminate function
- exception handling, termination
ms.assetid: 3ff1456a-7898-44bc-9266-a328a80b6006
ms.openlocfilehash: 7be81dec7fba80a273d635cbd30b96b09928bc66
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356449"
---
# <a name="setterminate-crt"></a>set_terminate (CRT)

Instaluje własną procedurę kończenia żądań ma zostać wywołana przez **zakończyć**.

## <a name="syntax"></a>Składnia

```cpp
terminate_function set_terminate( terminate_function termFunction );
```

### <a name="parameters"></a>Parametry

*termFunction*<br/>
Wskaźnik do funkcji zakończenia, który można zapisać.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do poprzedniej funkcji zarejestrowane przez **set_terminate** tak, aby funkcja poprzedniej można później przywrócić. Jeśli żadna funkcja poprzedniej została ustawiona, wartość zwracana mogą służyć do przywracania domyślne zachowanie; Ta wartość może być **NULL**.

## <a name="remarks"></a>Uwagi

**Set_terminate** funkcja instaluje *termFunction* jako funkcja wywoływana przez **zakończyć**. **set_terminate** jest używana z C++ obsługi wyjątków i może być wywoływana w dowolnym momencie w swoim programie, zanim wyjątku. **Zakończenie** wywołania [przerwać](abort.md) domyślnie. Możesz zmienić to ustawienie domyślne, pisanie funkcji zakończenia i wywołanie **set_terminate** o nazwie funkcji jako argumentem. **Zakończenie** wywołuje funkcję ostatniego podawana jako argument do **set_terminate**. Po zdatną żądanego zadania oczyszczania *termFunction* powinno zakończyć program. Jeśli go nie istnieje (jeśli jest on wraca do), [przerwać](abort.md) jest wywoływana.

W środowisku wielowątkowym zakończyć funkcje są obsługiwane osobno dla każdego wątku. Każdy nowy wątek musi zainstalować jego własnej funkcji zakończenia. W związku z tym każdy wątek jest odpowiedzialne za własną obsługę przerwania.

**Terminate_function —** typ jest zdefiniowany w EH. H jako wskaźnik do funkcji zdefiniowanych przez użytkownika zakończenia *termFunction* zwracającego **void**. Niestandardowej funkcji *termFunction* może nie przyjmują argumentów i nie powinny zwracać do obiektu wywołującego. Jeśli tak jest, [przerwać](abort.md) jest wywoływana. Nie może być zgłaszany wyjątek z poziomu *termFunction*.

```cpp
typedef void ( *terminate_function )( );
```

> [!NOTE]
> **Set_terminate** funkcja działa tylko poza debugerem.

Istnieje jeden **set_terminate** Obsługa wszystkie połączone dynamicznie biblioteki DLL lub exe; nawet wtedy, gdy wywołujesz **set_terminate** programu obsługi może być zastąpiona przez inną lub może być zastępowania ustawiony przez inny program obsługi Plik DLL lub EXE.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**set_terminate**|\<eh.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [zakończyć](terminate-crt.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków — procedury](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_terminate](get-terminate.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[Zakończenie](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
