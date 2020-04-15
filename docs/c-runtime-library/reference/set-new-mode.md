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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 3a27717d65714de54f477e4e2b3f243c4631fd8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332323"
---
# <a name="_set_new_mode"></a>_set_new_mode

Ustawia nowy tryb obsługi dla **malloc**.

## <a name="syntax"></a>Składnia

```cpp
int _set_new_mode( int newhandlermode );
```

### <a name="parameters"></a>Parametry

*newhandlermode*<br/>
Nowy tryb obsługi **dla malloc**; prawidłowa wartość wynosi 0 lub 1.

## <a name="return-value"></a>Wartość zwracana

Zwraca poprzedni zestaw trybu obsługi dla **malloc**. Zwracana wartość 1 wskazuje, że w przypadku braku alokacji pamięci **malloc** wcześniej nazywany nową procedurą obsługi; wartość zwracana 0 wskazuje, że nie. Jeśli argument *newhandlermode* nie jest równy 0 lub 1, zwraca wartość -1.

## <a name="remarks"></a>Uwagi

Funkcja **_set_new_mode** C++ ustawia nowy tryb obsługi dla [malloc](malloc.md). Nowy tryb obsługi wskazuje, czy w przypadku awarii **malloc** ma wywołać nową procedurę obsługi zgodnie z [_set_new_handler](set-new-handler.md). Domyślnie **malloc** nie wywołać nową procedurę obsługi na niepowodzenie alokacji pamięci. Można zastąpić to domyślne zachowanie, tak aby, gdy **malloc** nie można przydzielić pamięci, **malloc** wywołuje nową procedurę obsługi w taki sam sposób, jak **nowy** operator robi, gdy nie powiedzie się z tego samego powodu. Aby uzyskać więcej informacji, zobacz [nowe](../../cpp/new-operator-cpp.md) i [usuń](../../cpp/delete-operator-cpp.md) operatory w *odwołaniu do języka języka Języka C++*. Aby zastąpić wartość domyślną, zadzwoń:

```cpp
_set_new_mode(1);
```

na początku programu lub link z Newmode.obj (patrz [Opcje łącza).](../../c-runtime-library/link-options.md)

Ta funkcja sprawdza poprawność jego parametru. Jeśli *newhandlermode* jest czymś innym niż 0 lub 1, funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, <strong>_set_new_mode</strong> zwraca -1 i ustawia `EINVAL` **errno** na .

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_new_mode**|\<> new.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[Wolna](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
[_query_new_mode](query-new-mode.md)<br/>
