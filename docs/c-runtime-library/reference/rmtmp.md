---
title: _rmtmp — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- removing temporary files
- _rmtmp function
- files [C++], temporary
- rmtmp function
- files [C++], removing
- temporary files [C++], removing
ms.assetid: 7419501e-2587-4f2a-b469-0dca07f84736
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 050f1c93fc38b9fdf722682c9688336098a3da45
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405968"
---
# <a name="rmtmp"></a>_rmtmp

Usuwa pliki tymczasowe.

## <a name="syntax"></a>Składnia

```C

int _rmtmp( void );
```

## <a name="return-value"></a>Wartość zwracana

**_rmtmp —** zwraca liczbę plików tymczasowych zamknięty i usunięty.

## <a name="remarks"></a>Uwagi

**_Rmtmp —** funkcja czyści wszystkie pliki tymczasowe w bieżącym katalogu. Funkcja usuwa tylko te pliki, które zostały utworzone przez **tmpfile —**; go używać tylko w tym samym katalogu, w którym zostały utworzone pliki tymczasowe.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_rmtmp**|\<stdio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

Zobacz przykład [tmpfile —](tmpfile.md).

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_flushall](flushall.md)<br/>
[tmpfile](tmpfile.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
