---
title: INP, _inp, inpw, _inpw, _inpd
description: Opisuje funkcje INP, _inp, inpw, _inpw i _inpd w bibliotece środowiska uruchomieniowego języka Microsoft C (CRT).
ms.date: 12/09/2019
api_name:
- inp
- inpw
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
- inp
- inpw
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
ms.openlocfilehash: 48e0e58d2886c5a8bb90a86c81cb785d364666e8
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988715"
---
# <a name="inp-_inp-inpw-_inpw-_inpd"></a>INP, _inp, inpw, _inpw, _inpd

Dane wejściowe, z portu, bajtu (`inp`, `_inp`), wyrazu (`inpw`, `_inpw`) lub podwójnego wyrazu (`_inpd`).

> [!IMPORTANT]
> Te funkcje są przestarzałe. Począwszy od programu Visual Studio 2015, nie są one dostępne w CRT.  
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```cpp
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

### <a name="parameters"></a>Parametry

\ *portów*
Numer portu We/Wy.

## <a name="return-value"></a>Wartość zwrócona

Funkcje zwracają wartość bajtu, słowa lub podwójnego słowa odczytanego z `port`. Nie będzie zwrotu błędu.

## <a name="remarks"></a>Uwagi

`_inp`, `_inpw`, i `_inpd` funkcje odczytują bajt, wyraz i podwójne słowo, odpowiednio, z określonego portu wejściowego. Wartością wejściową może być każda nieoznaczona krótka liczba całkowita z zakresu od 0 do 65 535.

Ponieważ te funkcje odczytują się bezpośrednio z portu we/wy, nie można ich używać w kodzie użytkownika.

Nazwy `inp` i `inpw` są starsze, przestarzałe nazwy dla funkcji `_inp` i `_inpw`. Aby uzyskać więcej informacji, zobacz [nazwy funkcji POSIX](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).

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

\ [we/wy konsoli i portu](../c-runtime-library/console-and-port-i-o.md)
[Outp, outpw, _outp, _outpw _outpd](../c-runtime-library/outp-outpw-outpd.md)
