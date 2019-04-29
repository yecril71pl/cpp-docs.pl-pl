---
title: _set_new_mode
ms.date: 11/04/2016
apiname:
- _set_new_mode
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_new_mode
- _set_new_mode
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
ms.openlocfilehash: 0228170e4ab5b55b4b061fa61a412766de77a063
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356605"
---
# <a name="setnewmode"></a>_set_new_mode

Ustawia nowy tryb obsługi dla **— funkcja malloc**.

## <a name="syntax"></a>Składnia

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>Parametry

*newhandlermode*<br/>
Nowy tryb obsługi dla **— funkcja malloc**; prawidłowe wartości to 0 lub 1.

## <a name="return-value"></a>Wartość zwracana

Zwraca zestaw trybu dla poprzedniej procedury obsługi **— funkcja malloc**. Zwracana wartość 1 oznacza, że, w przypadku niepowodzenia, można przydzielić pamięci, **— funkcja malloc** wcześniej nazywane nową procedurę obsługi; zwracana wartość wynosząca 0 wskazuje, czy nie. Jeśli *newhandlermode* argument nie jest równa 0 lub 1, funkcja zwraca wartość -1.

## <a name="remarks"></a>Uwagi

C++ **_Set_new_mode** funkcja Ustawia nowy tryb obsługi dla [— funkcja malloc](malloc.md). Nowy tryb obsługi wskazuje, czy w przypadku awarii, **— funkcja malloc** ma wywoływać nową procedurę obsługi zgodnie z ustawieniem [_set_new_handler](set-new-handler.md). Domyślnie **— funkcja malloc** nie wywołuje nowej procedury obsługi awarii w celu przydzielenia pamięci. Można zastąpić to zachowanie domyślne tak, aby, gdy **— funkcja malloc** nie może przydzielić pamięci, **— funkcja malloc** wywoła nową procedurę obsługi w taki sam sposób **nowe** jest operator Jeśli jej nie powiedzie się z tego samego powodu. Aby uzyskać więcej informacji, zobacz [nowe](../../cpp/new-operator-cpp.md) i [Usuń](../../cpp/delete-operator-cpp.md) operatorów w *C++ Language Reference*. Aby zastąpić domyślne, wywołaj polecenie:

```cpp
_set_new_mode(1);
```

wczesne programu w lub Połącz z Newmode.obj (zobacz [opcje łącza](../../c-runtime-library/link-options.md)).

Ta funkcja sprawdza poprawność swojego parametru. Jeśli *newhandlermode* żadnych innych niż 0 lub 1, funkcja wywołuje procedurę obsługi nieprawidłowego parametru, jak opisano w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, <strong>_set_new_mode</strong> zwraca wartość -1 i ustawia **errno** do `EINVAL`.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_new_mode**|\<new.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
