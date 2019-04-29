---
title: set_unexpected (CRT)
ms.date: 11/04/2016
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
helpviewer_keywords:
- set_unexpected function
- unexpected function
- exception handling, termination
ms.assetid: ebcef032-4771-48e5-88aa-2a1ab8750aa6
ms.openlocfilehash: 6c38421e447ca7b3f263148f51f0ade5c59e2804
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356406"
---
# <a name="setunexpected-crt"></a>set_unexpected (CRT)

Instaluje własną funkcję zakończenia ma zostać wywołana przez **nieoczekiwany**.

## <a name="syntax"></a>Składnia

```cpp
unexpected_function set_unexpected( unexpected_function unexpFunction );
```

### <a name="parameters"></a>Parametry

*unexpFunction*<br/>
Wskaźnik do funkcji, który napisać, aby zastąpić **nieoczekiwany** funkcji.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do poprzedniej funkcji zakończenia rejestracji przez **_set_unexpected** tak, aby funkcja poprzedniej można później przywrócić. Jeśli żadna funkcja poprzedniej została ustawiona, wartość zwracana mogą służyć do przywracania domyślne zachowanie; Ta wartość może być **NULL**.

## <a name="remarks"></a>Uwagi

**Set_unexpected** funkcja instaluje *unexpFunction* jako funkcja wywoływana przez **nieoczekiwany**. **Nieoczekiwany** nie jest używany w bieżącej implementacji obsługi wyjątków C++. **Unexpected_function** typ jest zdefiniowany w EH. H jako wskaźnik do funkcji zdefiniowanej przez użytkownika nieoczekiwany, *unexpFunction* zwracającego **void**. Niestandardowe *unexpFunction* funkcji nie powinny zwracać do obiektu wywołującego.

```cpp
typedef void ( *unexpected_function )( );
```

Domyślnie **nieoczekiwany** wywołania **zakończyć**. To zachowanie domyślne można zmienić przez pisanie funkcji zakończenia i wywołanie **set_unexpected** o nazwie funkcji jako argumentem. **Nieoczekiwany** wywołuje funkcję ostatniego podawana jako argument do **set_unexpected**.

W odróżnieniu od funkcji niestandardowych zakończenia zainstalowane przez wywołanie **set_terminate**, wyjątek może zostać wygenerowany z poziomu *unexpFunction*.

W środowisku wielowątkowym nieoczekiwanych funkcji są obsługiwane osobno dla każdego wątku. Każdy nowy wątek musi zainstalować jego własnej funkcji nieoczekiwany. W związku z tym każdy wątek jest odpowiedzialny za własne nieoczekiwany obsługi.

W bieżącej implementacji Microsoft obsługę wyjątków C++ **nieoczekiwany** wywołania **zakończyć** domyślnie i nigdy nie jest wywoływana przez bibliotekę uruchomieniową obsługi wyjątków. Nie przynosi żadnej korzyści konkretnego wywołania **nieoczekiwany** zamiast **zakończyć**.

Istnieje jeden **set_unexpected** Obsługa wszystkie połączone dynamicznie biblioteki DLL lub exe; nawet wtedy, gdy wywołujesz **set_unexpected** programu obsługi może być zastąpiona przez inną, lub ustawiony przez program obsługi gestu inny plik DLL lub EXE.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**set_unexpected**|\<eh.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków — procedury](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_get_unexpected](get-unexpected.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[Zakończenie](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
