---
title: _getch, _getwch
description: Dokumentacja interfejsu API dla _getch i _getwch; który pobiera znak z konsoli bez echa.
ms.date: 4/2/2020
api_name:
- _getch
- _getwch
- _o__getch
- _o__getwch
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
- api-ms-win-crt-conio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- getwch
- _getch
- _getwch
helpviewer_keywords:
- characters, getting from console
- getch function
- _getwch function
- console, reading from
- _getch function
- getwch function
ms.assetid: cc116be7-cff2-4274-970f-5e7b18ccc05c
ms.openlocfilehash: 39954cdbe507baad05055770df5db8859737b9d1
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555856"
---
# <a name="_getch-_getwch"></a>_getch, _getwch

Pobiera znak z konsoli bez echa.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _getch( void );
wint_t _getwch( void );
```

## <a name="return-value"></a>Wartość zwracana

Zwraca odczyt znaku. Nie ma żadnego powrotu błędu.

## <a name="remarks"></a>Uwagi

Funkcje **_getch** i **_getwch** odczytają pojedynczy znak z konsoli bez echa znaku. Żadna z tych funkcji nie może być użyta do odczytu kombinacji klawiszy CTRL + C. Podczas odczytywania klucza funkcji lub klawisza Strzałka każda funkcja musi być wywoływana dwukrotnie. pierwsze wywołanie zwraca wartość 0 lub wartość 0xE0, a drugie wywołanie zwraca rzeczywisty kod klucza.

Te funkcje blokują wątek wywołujący i dlatego są bezpieczne wątkowo. W przypadku wersji bez blokowania zobacz [_getch_nolock, _getwch_nolock](getch-nolock-getwch-nolock.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_gettch**|**_getch**|**_getch**|**_getwch**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_getch**|\<conio.h>|
|**_getwch**|\<conio.h> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_getch.c
// compile with: /c
// This program reads characters from
// the keyboard until it receives a 'Y' or 'y'.

#include <conio.h>
#include <ctype.h>

int main( void )
{
   int ch;

   _cputs( "Type 'Y' when finished typing keys: " );
   do
   {
      ch = _getch();
      ch = toupper( ch );
   } while( ch != 'Y' );

   _putch( ch );
   _putch( '\r' );    // Carriage return
   _putch( '\n' );    // Line feed
}
```

```Input
abcdefy
```

```Output
Type 'Y' when finished typing keys: Y
```

## <a name="see-also"></a>Zobacz też

[We/wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_getche, _getwche](getche-getwche.md)<br/>
[_cgets, _cgetws](../../c-runtime-library/cgets-cgetws.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[_ungetch, _ungetwch, _ungetch_nolock, _ungetwch_nolock](ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)<br/>
