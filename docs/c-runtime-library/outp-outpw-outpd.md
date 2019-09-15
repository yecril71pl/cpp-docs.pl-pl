---
title: _outp, _outpw, _outpd
ms.date: 11/04/2016
api_name:
- _outpd
- _outp
- _outpw
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
ms.openlocfilehash: d1e7028ae833e1358ce3199b7e7079535c84d135
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944131"
---
# <a name="_outp-_outpw-_outpd"></a>_outp, _outpw, _outpd

Dane wyjściowe, w porcie, bajt (`_outp`), słowo (`_outpw`) lub podwójne słowo (`_outpd`).

> [!IMPORTANT]
>  Te funkcje są przestarzałe. Począwszy od programu Visual Studio 2015, nie są one dostępne w CRT.

> [!IMPORTANT]
>  Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```

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

#### <a name="parameters"></a>Parametry
*przewożąc*<br/>
Numer portu.

*databyte, dataword*<br/>
Wartości wyjściowe.

## <a name="return-value"></a>Wartość zwracana

Funkcje zwracają dane wyjściowe. Brak powrotu błędu.

## <a name="remarks"></a>Uwagi

`_outp`, ,`_outpw` I`_outpd` funkcje zapisują bajt, wyraz i podwójne słowo odpowiednio do określonego portu wyjściowego. Argument *portu* może być dowolną liczbą całkowitą bez znaku z zakresu 0 – 65 535; *databyte* może być dowolną liczbą całkowitą z zakresu 0-255; i *dataword* może być dowolną wartością z zakresu liczb całkowitych, niepodpisanej krótkiej liczby całkowitej i niepodpisanej Long Integer.

Ponieważ te funkcje zapisują bezpośrednio do portu we/wy, nie można ich używać w kodzie użytkownika. Aby uzyskać informacje o korzystaniu z portów we/wy w tych systemach operacyjnych, wyszukaj frazę "komunikacja szeregowa w systemie Win32" w witrynie MSDN.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`_outp`|\<conio.h>|
|`_outpw`|\<conio.h>|
|`_outpd`|\<conio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[We/wy konsoli i portu](../c-runtime-library/console-and-port-i-o.md)<br/>
[_inp, _inpw, _inpd](../c-runtime-library/inp-inpw-inpd.md)
