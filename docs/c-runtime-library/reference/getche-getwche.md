---
title: "_getche —, _getwche — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getwche
- _getche
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
- getwche
- _getche
- _getwche
dev_langs: C++
helpviewer_keywords:
- characters, getting from console
- _getwche function
- getche function
- console, reading from
- getwche function
- _getche function
ms.assetid: eac978a8-c43a-4130-938f-54f12e2a0fda
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ce45b5467032b7660202749117e60a1bb3b88b74
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="getche-getwche"></a>_getche, _getwche
Pobiera konsoli z echa znak.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _getche( void );  
wint_t _getwche( void );  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca znak do odczytu. Nie ma żadnych zwracany błąd.  
  
## <a name="remarks"></a>Uwagi  
 `_getche` i `_getwche` funkcji odczytu pojedynczy znak z poziomu konsoli z echa, co oznacza, że znak jest wyświetlany w konsoli. Żadna z tych funkcji można odczytać klawiszy CTRL + C. Podczas odczytywania klucza funkcji lub klawisz strzałki, każda funkcja musi być wywołana dwukrotnie; Zwraca pierwsze wywołanie 0 lub wartość 0xE0, natomiast drugie wywołanie rzeczywisty kod klucza.  
  
 Te funkcje Zablokuj wątek wywołujący i w związku z tym są wątkowo. Blokowania wersje można znaleźć [_getche_nolock —, _getwche_nolock —](../../c-runtime-library/reference/getche-nolock-getwche-nolock.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_getche`|`_getche`|`_getch`|`_getwche`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_getche`|\<conio.h >|  
|`_getwche`|\<conio.h > lub \<wchar.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_getche.c  
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
      ch = _getche();  
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
Type 'Y' when finished typing keys: abcdefyY  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)   
 [_cgets —, _cgetws —](../../c-runtime-library/cgets-cgetws.md)   
 [getc —, getwc —](../../c-runtime-library/reference/getc-getwc.md)   
 [_ungetch —, _ungetwch —, _ungetch_nolock — _ungetwch_nolock —](../../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)