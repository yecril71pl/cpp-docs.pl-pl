---
title: _inp, _inpw, _inpd
ms.date: 11/04/2016
api_name:
- _inp
- _inpw
- _inpd
api_location:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- inpd
- _inp
- _inpw
- _inpd
helpviewer_keywords:
- inp function
- inpw function
- ports, I/O routines
- inpd function
- _inp function
- _inpd function
- I/O [CRT], port
- _inpw function
ms.assetid: 5d9c2e38-fc85-4294-86d5-7282cc02d1b3
ms.openlocfilehash: 4668002fdf709e3e425ac379f136e228250896d4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944983"
---
# <a name="_inp-_inpw-_inpd"></a>_inp, _inpw, _inpd

Dane wejściowe, z portu, bajt (`_inp`), słowo (`_inpw`) lub podwójne słowo (`_inpd`).

> [!IMPORTANT]
>  Te funkcje są przestarzałe. Począwszy od programu Visual Studio 2015, nie są one dostępne w CRT.

> [!IMPORTANT]
>  Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```
int _inp(
   unsigned short port
);
unsigned short _inpw(
   unsigned short port
);
unsigned long _inpd(
   unsigned short port
);
```

#### <a name="parameters"></a>Parametry

*przewożąc*<br/>
Numer portu we/wy.

## <a name="return-value"></a>Wartość zwracana

Funkcje zwracają bajt, wyraz lub podwójne odczytywanie `port`wyrazów. Brak powrotu błędu.

## <a name="remarks"></a>Uwagi

`_inp`, ,`_inpw` I`_inpd` funkcje odczytują bajt, wyraz i podwójne słowo, odpowiednio, z określonego portu wejściowego. Wartością wejściową może być każda nieoznaczona krótka liczba całkowita z zakresu od 0 do 65 535.

Ponieważ te funkcje odczytują się bezpośrednio z portu we/wy, nie można ich używać w kodzie użytkownika.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`_inp`|\<conio.h>|
|`_inpw`|\<conio.h>|
|`_inpd`|\<conio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[We/wy konsoli i portu](../c-runtime-library/console-and-port-i-o.md)<br/>
[_outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)
