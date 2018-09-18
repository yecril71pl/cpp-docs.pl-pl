---
title: _inp —, _inpw —, _inpd — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _inp
- _inpw
- _inpd
apilocation:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- inpd
- _inp
- _inpw
- _inpd
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 23e3f28ddb96bb34b38b3dd90ff6720edb1d9224
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041353"
---
# <a name="inp-inpw-inpd"></a>_inp, _inpw, _inpd

Dane wejściowe z portu, bajt (`_inp`), słowo (`_inpw`), lub podwójne słowo (`_inpd`).

> [!IMPORTANT]
>  Te funkcje są przestarzałe. Począwszy od programu Visual Studio 2015, nie są one dostępne w CRT.

> [!IMPORTANT]
>  Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Port*<br/>
Numer portu We/Wy.

## <a name="return-value"></a>Wartość zwracana

Funkcje zwracają wartość bajtu, słowa lub podwójnego słowa odczytanego z `port`. Nie będzie zwrotu błędu.

## <a name="remarks"></a>Uwagi

`_inp`, `_inpw`, I `_inpd` funkcje odczytują bajt, wyraz i podwójne słowo, odpowiednio, z określonego portu wejściowego. Wartość wejściowa może być dowolnym niepodpisana krótka liczba całkowita z zakresu 0 - 65 535.

Ponieważ te funkcje czytają bezpośrednio z portu We/Wy, nie można użyć w kodzie użytkownika.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`_inp`|\<conio.h>|
|`_inpw`|\<conio.h>|
|`_inpd`|\<conio.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz też

[We/Wy konsoli i portu](../c-runtime-library/console-and-port-i-o.md)<br/>
[_outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)