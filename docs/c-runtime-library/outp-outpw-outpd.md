---
title: _outp, _outpw, _outpd
ms.date: 11/04/2016
apiname:
- _outpd
- _outp
- _outpw
apilocation:
- msvcrt.dll
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
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
ms.openlocfilehash: cb3e0c9fefd62b1af3c7dd6dda01278206d1bf49
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595523"
---
# <a name="outp-outpw-outpd"></a>_outp, _outpw, _outpd

Dane wyjściowe do portu, bajt (`_outp`), słowo (`_outpw`), lub podwójne słowo (`_outpd`).

> [!IMPORTANT]
>  Te funkcje są przestarzałe. Począwszy od programu Visual Studio 2015, nie są one dostępne w CRT.

> [!IMPORTANT]
>  Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
*Port*<br/>
Numer portu.

*databyte, dataword*<br/>
Wartości wyjściowe.

## <a name="return-value"></a>Wartość zwracana

Funkcje zwracają dane wyjściowe. Nie będzie zwrotu błędu.

## <a name="remarks"></a>Uwagi

`_outp`, `_outpw`, I `_outpd` funkcje zapisują bajt, wyraz i podwójne słowo, odpowiednio do portu określonym produktem wyjściowym. *Portu* argument może być liczbą całkowitą bez znaku z zakresu 0 - 65 535; *databyte* może być liczbą całkowitą z zakresu 0 - 255; i *dataword* może być dowolną wartość z zakresu, liczba całkowita, niepodpisane krótka liczba całkowita i niepodpisane długa liczba całkowita, odpowiednio.

Ponieważ te funkcje zapisują bezpośrednio do portu We/Wy, nie można użyć w kodzie użytkownika. Aby uzyskać informacje dotyczące korzystania z portów We/Wy w tych systemach operacyjnych wyszukaj ciąg "Komunikacja szeregowa w Win32" w witrynie MSDN.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`_outp`|\<conio.h>|
|`_outpw`|\<conio.h>|
|`_outpd`|\<conio.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz też

[We/Wy konsoli i portu](../c-runtime-library/console-and-port-i-o.md)<br/>
[_inp, _inpw, _inpd](../c-runtime-library/inp-inpw-inpd.md)