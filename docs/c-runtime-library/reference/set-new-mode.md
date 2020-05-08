---
title: _set_new_mode
ms.date: 4/2/2020
api_name:
- _set_new_mode
- _o__set_new_mode
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_new_mode
- _set_new_mode
helpviewer_keywords:
- handler modes
- _set_new_mode function
- set_new_mode function
ms.assetid: 4d14039a-e54e-4689-8c70-74a4b9834768
ms.openlocfilehash: f3635d462d2c7438ce985d74ff347120c02c82e0
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920099"
---
# <a name="_set_new_mode"></a>_set_new_mode

Ustawia nowy tryb obsługi dla opcji **malloc**.

## <a name="syntax"></a>Składnia

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>Parametry

*newhandlermode*<br/>
Nowy tryb obsługi dla opcji **malloc**; prawidłowa wartość to 0 lub 1.

## <a name="return-value"></a>Wartość zwracana

Zwraca poprzedni tryb obsługi ustawiony dla opcji **malloc**. Zwracana wartość 1 oznacza, że w przypadku niepowodzenia przydzielenia pamięci, **malloc** wcześniej nosiła nową procedurę obsługi; zwracana wartość 0 wskazuje, że nie. Jeśli argument *newhandlermode* nie jest równy 0 lub 1, zwraca-1.

## <a name="remarks"></a>Uwagi

Funkcja C++ **_set_new_mode** ustawia nowy tryb obsługi dla opcji [malloc](malloc.md). Nowy tryb obsługi wskazuje, czy w przypadku niepowodzenia, **malloc** ma wywołać nową procedurę obsługi jako ustawioną przez [_set_new_handler](set-new-handler.md). Domyślnie funkcja **malloc** nie wywołuje nowej procedury obsługi w przypadku niepowodzenia przydzielenia pamięci. Można zastąpić to zachowanie domyślne, tak aby w przypadku niepowodzenia przydzielenia pamięci przez funkcję **malloc** wywołuje nową procedurę obsługi w taki sam **sposób, w** jaki operator **New** wykonuje, gdy nie powiedzie się z tego samego powodu. Aby uzyskać więcej informacji, zobacz Operatory [New](../../cpp/new-operator-cpp.md) i [delete](../../cpp/delete-operator-cpp.md) w *dokumentacji języka C++*. Aby zastąpić wartość domyślną, należy wywołać:

```cpp
_set_new_mode(1);
```

Wczesne w programie lub Połącz z NewMode. obj (zobacz [Opcje linku](../../c-runtime-library/link-options.md)).

Ta funkcja sprawdza poprawność parametru. Jeśli *newhandlermode* jest coś innego niż 0 lub 1, funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, <strong>_set_new_mode</strong> zwraca wartość-1 i **errno** ustawia errno `EINVAL`na.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_new_mode**|\<Nowy. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[zwolniony](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
