---
title: _rmtmp
ms.date: 11/04/2016
apiname:
- _rmtmp
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- rmtmp
- _rmtmp
helpviewer_keywords:
- removing temporary files
- _rmtmp function
- files [C++], temporary
- rmtmp function
- files [C++], removing
- temporary files [C++], removing
ms.assetid: 7419501e-2587-4f2a-b469-0dca07f84736
ms.openlocfilehash: bf4f2cff48e8660682fc8a00d10d9a1fe960a6a7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357426"
---
# <a name="rmtmp"></a>_rmtmp

Powoduje usunięcie plików tymczasowych.

## <a name="syntax"></a>Składnia

```C

int _rmtmp( void );
```

## <a name="return-value"></a>Wartość zwracana

**_rmtmp —** zwraca liczbę plików tymczasowych, zamknięte, a następnie usuwane.

## <a name="remarks"></a>Uwagi

**_Rmtmp —** funkcja czyści wszystkie pliki tymczasowe w bieżącym katalogu. Funkcja usuwa tylko pliki tworzone przez **tmpfile —**; go używać tylko w tym samym katalogu, w którym zostały utworzone pliki tymczasowe.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_rmtmp**|\<stdio.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

Zobacz przykład [tmpfile —](tmpfile.md).

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[_flushall](flushall.md)<br/>
[tmpfile](tmpfile.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
