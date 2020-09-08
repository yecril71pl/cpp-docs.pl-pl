---
title: hypot, hypotf, hypotl, _hypot, _hypotf, _hypotl
description: Dokumentacja interfejsu API dla hypot —, hypotf —, hypotl, _hypot, _hypotf i _hypotl; który obliczy przeciwprostokątnej.
ms.date: 9/1/2020
api_name:
- _hypotf
- hypot
- hypotf
- _hypot
- _hypotl
- hypotl
- _o__hypot
- _o__hypotf
- _o_hypot
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
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- hypotf
- hypotl
- _hypotl
- hypot
- _hypot
- _hypotf
helpviewer_keywords:
- hypotenuse calculation
- hypot function
- hypotf function
- triangles, calculating hypotenuse
- hypotl function
- calculating hypotenuses
- _hypot function
ms.assetid: 6a13887f-bd53-43fc-9d77-5b42d6e49925
ms.openlocfilehash: 199e330dcd78c372a0279cac9f0e96cb47c561e8
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556453"
---
# <a name="hypot-hypotf-hypotl-_hypot-_hypotf-_hypotl"></a>hypot, hypotf, hypotl, _hypot, _hypotf, _hypotl

Oblicza przeciwprostokątnej.

## <a name="syntax"></a>Składnia

```C
double hypot(
   double x,
   double y
);
float hypotf(
   float x,
   float y
);
long double hypotl(
   long double x,
   long double y
);
double _hypot(
   double x,
   double y
);
float _hypotf(
   float x,
   float y
);
long double _hypotl(
   long double x,
   long double y
);
#define hypotf(X, Y) // Requires C11 or higher
```

### <a name="parameters"></a>Parametry

*x*, *y*\
Wartości zmiennoprzecinkowe.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, **hypot —** zwraca długość przeciwprostokątnej; w przypadku przepełnienia funkcja **hypot —** zwraca plik inf (nieskończoność), a zmienna **errno** jest ustawiona na **ERANGE**. Za pomocą **_matherr** można modyfikować obsługę błędów.

Aby uzyskać więcej informacji na temat kodów powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **hypot —** oblicza długość przeciwprostokątneju prawego trójkąta, uwzględniając długość dwóch boków *x* i *y* (innymi słowy, pierwiastek kwadratowy *x*<sup>2</sup>  +  *y*<sup>2</sup>).

Wersje funkcji, które mają wiodące znaki podkreślenia, są zapewniane pod kątem zgodności z wcześniejszymi standardami. Ich zachowanie jest identyczne z wersjami, które nie mają wiodących podkreśleń. Zalecamy używanie wersji bez wiodących podkreśleń dla nowego kodu.

Jeśli używasz \<tgmath.h> `hypot()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**hypot —**, **hypotf —**, **hypotl**, **_hypot**, **_hypotf**, **_hypotl**|\<math.h>|
|**hypot —** — makro | \<tgmath.h> |

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_hypot.c
// This program prints the hypotenuse of a right triangle.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 3.0, y = 4.0;

   printf( "If a right triangle has sides %2.1f and %2.1f, "
           "its hypotenuse is %2.1f\n", x, y, _hypot( x, y ) );
}
```

```Output
If a right triangle has sides 3.0 and 4.0, its hypotenuse is 5.0
```

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[_cabs](cabs.md)<br/>
[_matherr](matherr.md)<br/>
