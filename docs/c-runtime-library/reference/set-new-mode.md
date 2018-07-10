---
title: _set_new_mode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b914e950fd94435768c355f327d3d48a653e0d5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407148"
---
# <a name="setnewmode"></a>_set_new_mode

Ustawia tryb obsługi nowych **— funkcja malloc**.

## <a name="syntax"></a>Składnia

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>Parametry

*newhandlermode*<br/>
Nowy tryb obsługi na **— funkcja malloc**; prawidłowe wartości to 0 lub 1.

## <a name="return-value"></a>Wartość zwracana

Zwraca poprzednią procedurę obsługi trybu zestawie **— funkcja malloc**. Zwracana wartość 1 oznacza, że, nie można przydzielić pamięci, **— funkcja malloc** wcześniej nazywane nowe procedury obsługi; wartość zwracana 0 wskazuje nie zostało. Jeśli *newhandlermode* argument nie jest równa 0 lub 1, zwraca -1.

## <a name="remarks"></a>Uwagi

C++ **_set_new_mode —** funkcja ustawia tryb obsługi nowych [— funkcja malloc](malloc.md). Nowy tryb obsługi wskazuje, czy w przypadku awarii, **— funkcja malloc** jest wywołanie nowe procedury obsługi zgodnie z ustawieniami [_set_new_handler —](set-new-handler.md). Domyślnie **— funkcja malloc** nie wywołuje nowe procedury obsługi nie można przydzielić pamięci. Można zastąpić to zachowanie domyślne, aby, gdy **— funkcja malloc** nie może przydzielić pamięci, **— funkcja malloc** wywołuje nowe procedury obsługi w taki sam jak robi **nowe** operator jest Jeśli go nie powiodło się z tego samego powodu. Aby uzyskać więcej informacji, zobacz [nowe](../../cpp/new-operator-cpp.md) i [usunąć](../../cpp/delete-operator-cpp.md) operatory w *dokumentacja języka C++*. Aby zastąpić domyślną, należy wywołać:

```cpp
_set_new_mode(1);
```

wczesne programu w lub Połącz z Newmode.obj (zobacz [opcje łącza](../../c-runtime-library/link-options.md)).

Ta funkcja weryfikuje jej parametr. Jeśli *newhandlermode* żadnych innych niż 0 lub 1, funkcja wywołuje program obsługi nieprawidłowych parametrów, jak opisano w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **_ *** set_new_mode —** zwraca wartość -1 i ustawia **errno** do **einval —**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_new_mode**|\<new.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
