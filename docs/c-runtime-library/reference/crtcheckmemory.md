---
title: _CrtCheckMemory
ms.date: 11/04/2016
api_name:
- _CrtCheckMemory
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
- CrtCheckMemory
- _CrtCheckMemory
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
ms.openlocfilehash: 7e458825a81b7032310458ccda52d9299e126a35
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938859"
---
# <a name="_crtcheckmemory"></a>_CrtCheckMemory

Potwierdza integralność bloków pamięci przydzieloną w stercie debugowania (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C

int _CrtCheckMemory( void );
```

## <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia funkcja **_CrtCheckMemory** zwraca wartość true; w przeciwnym razie funkcja zwraca wartość FALSE.

## <a name="remarks"></a>Uwagi

Funkcja **_CrtCheckMemory** sprawdza poprawność pamięci przydzielonej przez menedżera sterty debugowania, weryfikując bazowe stertę podstawową i sprawdzając każdy blok pamięci. Jeśli wystąpi błąd lub niespójność pamięci w podstawowym stosie bazowym, informacje nagłówka debugowania lub bufory zastępowania, **_CrtCheckMemory** generuje raport debugowania zawierający informacje opisujące warunek błędu. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtCheckMemory** są usuwane podczas przetwarzania wstępnego.

Zachowanie **_CrtCheckMemory** może być kontrolowane przez ustawienie pól bitowych flagi [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) przy użyciu funkcji [_CrtSetDbgFlag](crtsetdbgflag.md) . Włączenie pola bitowego **_CRTDBG_CHECK_ALWAYS_DF** na wyniki w **_CrtCheckMemory** jest wywoływana za każdym razem, gdy wymagana jest operacja alokacji pamięci. Chociaż ta metoda spowalnia wykonywanie, jest przydatna do szybkiego przechwytywania błędów. Wyłączenie pola bitu **_CRTDBG_ALLOC_MEM_DF** powoduje, że **_CrtCheckMemory** nie sprawdza sterty i natychmiast zwraca **wartość true**.

Ponieważ ta funkcja zwraca **wartość true** lub **false**, można ją przesłać do jednego z makr [_ASSERT](assert-asserte-assert-expr-macros.md) w celu utworzenia prostego mechanizmu obsługi błędów debugowania. Poniższy przykład powoduje niepowodzenie potwierdzenia w przypadku wykrycia uszkodzenia w stercie:

```C
_ASSERTE( _CrtCheckMemory( ) );
```

Aby uzyskać więcej informacji o tym, jak **_CrtCheckMemory** może być używany z innymi funkcjami debugowania, zobacz [funkcje raportowania stanu sterty](/visualstudio/debugger/crt-debug-heap-details). Aby zapoznać się z omówieniem zarządzania pamięcią i sterty debugowania, zobacz [szczegóły sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtCheckMemory**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje wyłącznie [bibliotek uruchomieniowych C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Przykład

Aby zapoznać się z przykładem sposobu korzystania z **_CrtCheckMemory**, zobacz [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
