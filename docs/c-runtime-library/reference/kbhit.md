---
title: _kbhit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _kbhit
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
- _kbhit
- kbhit
- conio/_kbhit
dev_langs:
- C++
helpviewer_keywords:
- keyboard input
- user input, checking for keyboard
- kbhit function
- console
- console, checking
- keyboards, keyboard input
- _kbhit function
- keyboards, checking input
ms.assetid: e82a1cc9-bbec-4150-b678-a7e433220fe4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f414403774a6f2dbd5e21b70d707ab8c8b20c63f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399052"
---
# <a name="kbhit"></a>_kbhit

Sprawdza, czy konsoli dla klawiatury.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C

int _kbhit( void );
```

## <a name="return-value"></a>Wartość zwracana

**_kbhit —** zwraca wartość niezerową, jeśli klucz został naciśnięty. W przeciwnym razie zwraca wartość 0.

## <a name="remarks"></a>Uwagi

**_Kbhit —** funkcja sprawdza konsoli dla ostatnich naciśnięcie klawisza. Jeśli funkcja zwraca wartość niezerową, naciśnięcie klawisza oczekuje się w buforze. Program może wywoływać **_getch —** lub **_getche —** uzyskać naciśnięcie klawisza.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_kbhit**|\<conio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_kbhit.c
// compile with: /c
/* This program loops until the user
* presses a key. If _kbhit returns nonzero, a
* keystroke is waiting in the buffer. The program
* can call _getch or _getche to get the keystroke.
*/

#include <conio.h>
#include <stdio.h>

int main( void )
{
   /* Display message until key is pressed. */
   while( !_kbhit() )
      _cputs( "Hit me!! " );

   /* Use _getch to throw key away. */
   printf( "\nKey struck was '%c'\n", _getch() );
}
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
Hit me!! Hit me!! Hit me!! Hit me!! Hit me!! Hit me!! Hit me!!
Key struck was 'q'
```

## <a name="see-also"></a>Zobacz także

[We/Wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
