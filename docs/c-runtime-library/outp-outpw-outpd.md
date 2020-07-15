---
title: Outp, outpw, _outp, _outpw _outpd
description: Opisuje przestarzałe i usunięte funkcje Outp, outpw, _outp, _outpw i _outpd biblioteki środowiska uruchomieniowego języka Microsoft C (CRT).
ms.date: 12/09/2019
api_name:
- _outpd
- _outp
- _outpw
- outp
- outpw
api_location:
- msvcrt.dll
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _outpw
- _outpd
- _outp
- outp
- outpw
- outpd
helpviewer_keywords:
- outpw function
- words
- _outpd function
- outpd function
- outp function
- ports, writing bytes at
- bytes, writing to ports
- words, writing to ports
- double words
- double words, writing to ports
- _outpw function
- _outp function
ms.assetid: c200fe22-41f6-46fd-b0be-ebb805b35181
ms.openlocfilehash: 0d28511cdf7487226635c0317b7c0ba21ab1d1be
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373479"
---
# <a name="outp-outpw-_outp-_outpw-_outpd"></a>Outp, outpw, _outp, _outpw _outpd

Dane wyjściowe, w porcie, bajt ( `outp` , `_outp` ), słowo ( `outpw` , `_outpw` ) lub podwójne słowo ( `_outpd` ).

> [!IMPORTANT]
> Te funkcje są przestarzałe. Począwszy od programu Visual Studio 2015, nie są one dostępne w CRT. \
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```cpp
int _outp(
   unsigned short port,
   int databyte
);
unsigned short _outpw(
   unsigned short port,
   unsigned short dataword
);
unsigned long _outpd(
   unsigned short port,
   unsigned long dataword
);
```

### <a name="parameters"></a>Parametry

*przewożąc*\
Numer portu.

*databyte, dataword*\
Wartości wyjściowe.

## <a name="return-value"></a>Wartość zwracana

Funkcje zwracają dane wyjściowe. Brak powrotu błędu.

## <a name="remarks"></a>Uwagi

`_outp`, `_outpw` , I `_outpd` funkcje zapisują bajt, wyraz i podwójne słowo odpowiednio do określonego portu wyjściowego. Argument *portu* może być dowolną liczbą całkowitą bez znaku z zakresu 0 – 65 535; *databyte* może być dowolną liczbą całkowitą z zakresu 0-255; i *dataword* może być dowolną wartością z zakresu liczb całkowitych, niepodpisanej krótkiej liczby całkowitej i niepodpisanej Long Integer.

Ponieważ te funkcje zapisują bezpośrednio do portu we/wy, nie można ich używać w kodzie systemu Windows w trybie użytkownika. Informacje o korzystaniu z portów we/wy w systemie operacyjnym Windows znajdują się w temacie [komunikacja szeregowa](https://docs.microsoft.com/previous-versions/ff802693(v=msdn.10)).

`outp`Nazwy i `outpw` są starsze, przestarzałe nazwy dla `_outp` `_outpw` funkcji i. Aby uzyskać więcej informacji, zobacz [nazwy funkcji POSIX](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`_outp`|\<conio.h>|
|`_outpw`|\<conio.h>|
|`_outpd`|\<conio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz też

[We/wy konsoli i portu](../c-runtime-library/console-and-port-i-o.md)\
[INP, inpw, _inp, _inpw _inpd](../c-runtime-library/inp-inpw-inpd.md)
