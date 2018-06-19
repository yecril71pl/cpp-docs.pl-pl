---
title: _getche_nolock —, _getwche_nolock — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _getche_nolock
- _getwche_nolock
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
apitype: DLLExport
f1_keywords:
- _getche_nolock
- _gettche_nolock
- _getwche_nolock
- getche_nolock
- getwche_nolock
- gettche_nolock
dev_langs:
- C++
helpviewer_keywords:
- characters, getting from console
- _gettche_nolock function
- getwche_nolock function
- _getche_nolock function
- getche_nolock function
- console, reading from
- _getwche_nolock function
- gettche_nolock function
ms.assetid: 9e853ad4-4d8a-4442-9ae5-da4b434f0b8c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e83d398330e2c7fbbf80ca5b14ef7b1099e56bc4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400105"
---
# <a name="getchenolock-getwchenolock"></a>_getche_nolock, _getwche_nolock

Pobiera znak z poziomu konsoli z echa i bez blokowania wątku.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _getche_nolock( void );
wint_t _getwche_nolock( void );
```

## <a name="return-value"></a>Wartość zwracana

Zwraca znak do odczytu. Nie ma żadnych zwracany błąd.

## <a name="remarks"></a>Uwagi

**_getche_nolock —** i **_getwche_nolock —** są takie same jak **_getche —** i **_getwche —** z tą różnicą, że ich nie chronione przed zakłóceniami przez inne wątki. Może być szybsze, ponieważ nie wiążą się z obciążenie zablokowania inne wątki. Ich używać tylko w kontekstach wątkowo, np. aplikacje jednowątkowe lub gdzie wywoływania zakres już obsługuje izolacji wątku.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_gettche_nolock —**|**_getche_nolock**|**_getch_nolock**|**_getwche_nolock**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_getche_nolock**|\<conio.h>|
|**_getwche_nolock**|\<conio.h > lub \<wchar.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_getche_nolock.c
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
      ch = _getche_nolock();
      ch = toupper( ch );
   } while( ch != 'Y' );

   _putch_nolock( ch );
   _putch_nolock( '\r' );    // Carriage return
   _putch_nolock( '\n' );    // Line feed
}
```

```Input
abcdefy
```

```Output
Type 'Y' when finished typing keys: abcdefyY
```

## <a name="see-also"></a>Zobacz także

[We/Wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cgets, _cgetws](../../c-runtime-library/cgets-cgetws.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[_ungetch, _ungetwch, _ungetch_nolock, _ungetwch_nolock](ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)<br/>
