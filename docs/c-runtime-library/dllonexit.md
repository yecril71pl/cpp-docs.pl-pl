---
title: __dllonexit
ms.date: 11/04/2016
api_name:
- __dllonexit
api_location:
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcr120_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __dllonexit
helpviewer_keywords:
- __dllonexit
ms.assetid: 708f2ceb-f95c-46b0-a58d-d68b3fa36f12
ms.openlocfilehash: 61d63c751dd755bf8a7680c674681e114945814b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940432"
---
# <a name="__dllonexit"></a>__dllonexit

Rejestruje procedurę, która ma zostać wywołana w czasie zakończenia.

## <a name="syntax"></a>Składnia

```
_onexit_t __dllonexit(   _onexit_t func,
   _PVFV **  pbegin,
   _PVFV **  pend
   )
```

#### <a name="parameters"></a>Parametry

*func*<br/>
Wskaźnik do funkcji, która ma zostać wykonana po zakończeniu.

*pbegin*<br/>
Wskaźnik do zmiennej wskazującej na początek listy funkcji do wykonania podczas odłączania.

*ustawić*<br/>
Wskaźnik do zmiennej wskazującej na koniec listy funkcji do wykonania podczas odłączania.

## <a name="return-value"></a>Wartość zwracana

Jeśli powiedzie się, wskaźnik do funkcji użytkownika. W przeciwnym razie wskaźnik o **wartości null** .

## <a name="remarks"></a>Uwagi

Funkcja jest analogiczna do funkcji _onexit, z tą różnicą, że zmienne globalne używane przez tę funkcję nie są widoczne dla tej procedury. [](../c-runtime-library/reference/onexit-onexit-m.md) `__dllonexit` Zamiast zmiennych globalnych, ta funkcja używa `pbegin` parametrów i. `pend`

Funkcje `_onexit` i`atexit` w bibliotece DLL połączonej z msvcrt. Biblioteka LIB musi obsługiwać własną listę atexit —/_onexit. Ta procedura jest procesem roboczym, który jest wywoływany przez takie biblioteki DLL.

Typ jest zdefiniowany jako `typedef void (__cdecl *_PVFV)(void)`. `_PVFV`

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany plik|
|-------------|-------------------|
|__dllonexit|OnExit. c|

## <a name="see-also"></a>Zobacz także

[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)
