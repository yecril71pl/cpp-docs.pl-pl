---
title: "_setmode — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _setmode
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
f1_keywords: _setmode
dev_langs: C++
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d894433ea7ad4c0525c044e64aa1e9c6f66459e3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="setmode"></a>_setmode
Ustawia tryb tłumaczenia pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
int _setmode (  
   int fd,  
   int mode   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fd`  
 Plik deskryptora.  
  
 `mode`  
 Nowy tryb tłumaczenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca poprzedniej tryb tłumaczenia.  
  
 Jeśli nieprawidłowe parametry są przekazywane do tej funkcji, program obsługi nieprawidłowy parametr zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, ta funkcja zwraca wartość -1 i zestawy `errno` albo `EBADF`, co oznacza deskryptora nieprawidłowy plik lub `EINVAL`, co wskazuje nieprawidłową `mode` argumentu.  
  
 Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `_setmode` Funkcja ustawia `mode` tryb tłumaczenia pliku określonego przez `fd`. Przekazywanie `_O_TEXT` jako `mode` ustawia tekst (translacji) trybu. Zwracany wiersz karetki źródła kombinacji (CR LF) są przekształcane na jeden wiersz źródła znaku w danych wejściowych. Wiersz źródła znaki są tłumaczone na kombinacje CR LF w danych wyjściowych. Przekazywanie `_O_BINARY` zestawów (niezrozumiały) trybie binarnym, w którym te tłumaczenia są pomijane.  
  
 Można również przekazać `_O_U16TEXT`, `_O_U8TEXT`, lub `_O_WTEXT` Aby włączyć tryb Unicode, jak pokazano w drugim przykładzie w dalszej części tego dokumentu. `_setmode`Zazwyczaj jest używane do modyfikowania domyślny tryb tłumaczenia `stdin` i `stdout`, ale można go używać na dowolnym pliku. W przypadku zastosowania `_setmode` do deskryptorów plików dla strumienia, wywołaj `_setmode` przed wykonaniem żadnych operacji na strumieniu wejściowych lub wyjściowych.  
  
> [!CAUTION]
>  Jeśli zapisywania danych do strumienia pliku, jawnie opróżnić kodu za pomocą [fflush —](../../c-runtime-library/reference/fflush.md) przed użyciem `_setmode` do zmieniania trybu. Jeśli nie mogło opróżnić kod, mogą uzyskać nieoczekiwane zachowanie. Jeśli dane nie zostały zapisane strumienia, nie trzeba opróżnić kod.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|----------------------|  
|`_setmode`|\<IO.h >|\<fcntl.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_setmode.c  
// This program uses _setmode to change  
// stdin from text mode to binary mode.  
  
#include <stdio.h>  
#include <fcntl.h>  
#include <io.h>  
  
int main( void )  
{  
   int result;  
  
   // Set "stdin" to have binary mode:  
   result = _setmode( _fileno( stdin ), _O_BINARY );  
   if( result == -1 )  
      perror( "Cannot set mode" );  
   else  
      printf( "'stdin' successfully changed to binary mode\n" );  
}  
```  
  
```Output  
'stdin' successfully changed to binary mode  
```  
  
## <a name="example"></a>Przykład  
  
```  
// crt_setmodeunicode.c  
// This program uses _setmode to change  
// stdout to Unicode. Cyrillic and Ideographic  
// characters will appear on the console (if  
// your console font supports those character sets).  
  
#include <fcntl.h>  
#include <io.h>  
#include <stdio.h>  
  
int main(void) {  
    _setmode(_fileno(stdout), _O_U16TEXT);  
    wprintf(L"\x043a\x043e\x0448\x043a\x0430 \x65e5\x672c\x56fd\n");  
    return 0;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa plików](../../c-runtime-library/file-handling.md)   
 [_creat —, _wcreat —](../../c-runtime-library/reference/creat-wcreat.md)   
 [fopen —, _wfopen —](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_otwórz, _wopen —](../../c-runtime-library/reference/open-wopen.md)   
 [_set_fmode —](../../c-runtime-library/reference/set-fmode.md)