---
title: "_cprintf_s —, _cprintf_s_l —, _cwprintf_s —, _cwprintf_s_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _cwprintf_s_l
- _cprintf_s_l
- _cprintf_s
- _cwprintf_s
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
- _cwprintf_s_l
- _cprintf_s
- cwprintf_s
- _cprintf_s_l
- cwprintf_s_l
- cprintf_s_l
- _tcprintf_s
- cprintf_s
- _cwprintf_s
- tcprintf_s
dev_langs: C++
helpviewer_keywords:
- tcprintf_s_l function
- _cprintf_s_l function
- _cwprintf_s_l function
- tcprintf_s function
- _tcprintf_s_l function
- _cwprintf_s function
- cwprintf_s function
- _cprintf_s function
- cprintf_s function
- _tcprintf_s function
- cprintf_s_l function
- cwprintf_s_l function
ms.assetid: c28504fe-0d20-4f06-8f97-ee33225922ad
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6a981de98d801db290833717788d5ae9b9bc4360
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cprintfs-cprintfsl-cwprintfs-cwprintfsl"></a>_cprintf_s, _cprintf_s_l, _cwprintf_s, _cwprintf_s_l
Formatuje i drukowanie do konsoli. Te wersje programu [_cprintf —, _cprintf_l —, _cwprintf —, _cwprintf_l —](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _cprintf_s(   
   const char * format [,   
   argument] ...   
);  
int _cprintf_s_l(   
   const char * format,  
   locale_t locale [,   
   argument] ...   
);  
int _cwprintf_s(  
   const wchar * format [,   
   argument] ...  
);  
int _cwprintf_s_l(  
   const wchar * format,  
   locale_t locale [,   
   argument] ...  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `format`  
 Ciąg kontroli formatu.  
  
 `argument`  
 Parametry opcjonalne.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Liczba znaków, wydrukować.  
  
## <a name="remarks"></a>Uwagi  
 Te funkcje formatowania i drukowania serii znaków i wartości bezpośrednio z konsoli programu przy użyciu `_putch` — funkcja (`_putwch` dla `_cwprintf_s`) znaków danych wyjściowych. Każdy `argument` (jeśli istnieje) jest konwertowana i dane wyjściowe według specyfikacji formatu w `format`. Format ma takie same tworzą i działać jako `format` parametr [printf_s —](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) funkcji. W odróżnieniu od `fprintf_s`, `printf_s`, i `sprintf_s` funkcji ani `_cprintf_s` ani `_cwprintf_s` tłumaczy znaki wysuwu wiersza na kombinacji powrotu wiersza kanału informacyjnego (CR LF) karetki podczas drukowania.  
  
 Jest to ważna różnica `_cwprintf_s` Wyświetla znaków Unicode, gdy jest używany w systemie Windows NT. W odróżnieniu od `_cprintf_s`, `_cwprintf_s` używa bieżące ustawienia regionalne konsoli  
  
 Wersje tych funkcji z `_l` sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżących ustawień regionalnych.  
  
> [!IMPORTANT]
>  Upewnij się, że `format` nie jest ciągiem zdefiniowane przez użytkownika.  
  
 Wersje niezabezpieczone, takich jak (zobacz [_cprintf —, _cprintf_l —, _cwprintf —, _cwprintf_l —](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)), te funkcje walidację ich parametrów i Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md), jeśli `format` jest wskaźnika o wartości null. Funkcje te różnią się od wersji niezabezpieczonego sprawdzania poprawności sam ciąg formatu. W przypadku dowolnego nieznany lub niewłaściwie sformułowany specyfikatory formatowania tych funkcji Wywołaj program obsługi nieprawidłowych parametrów. We wszystkich przypadkach, jeśli jest dozwolone wykonywanie, aby kontynuować, funkcje Zwróć -1 i ustaw `errno` do `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcprintf_s`|`_cprintf_s`|`_cprintf_s`|`_cwprintf_s`|  
|`_tcprintf_s_l`|`_cprintf_s_l`|`_cprintf_s_l`|`_cwprintf_s_l`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_cprintf_s`,`_cprintf_s_l`|\<conio.h >|  
|`_cwprintf_s`, `_cwprintf_s_l`|\<conio.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_cprintf_s.c  
// compile with: /c  
// This program displays some variables to the console.  
  
#include <conio.h>  
  
int main( void )  
{  
   int      i = -16, h = 29;  
   unsigned u = 62511;  
   char     c = 'A';  
   char     s[] = "Test";  
  
   /* Note that console output does not translate \n as  
    * standard output does. Use \r\n instead.  
    */  
   _cprintf_s( "%d  %.4x  %u  %c %s\r\n", i, h, u, c, s );  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
-16  001d  62511  A Test  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)   
 [_cscanf —, _cscanf_l —, _cwscanf — _cwscanf_l —](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)   
 [fprintf_s —, _fprintf_s_l —, fwprintf_s — _fwprintf_s_l —](../../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)   
 [printf_s —, _printf_s_l —, wprintf_s — _wprintf_s_l —](../../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [sprintf_s —, _sprintf_s_l —, swprintf_s — _swprintf_s_l —](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)   
 [vfprintf_s —, _vfprintf_s_l —, vfwprintf_s — _vfwprintf_s_l —](../../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)   
 [Składnia specyfikacji formatu: funkcje printf i wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)