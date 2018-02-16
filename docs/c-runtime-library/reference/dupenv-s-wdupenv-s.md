---
title: "_dupenv_s —, _wdupenv_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _dupenv_s
- _wdupenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- tdupenv_s
- _dupenv_s
- wdupenv_s
- dupenv_s
- _tdupenv_s
- _wdupenv_s
dev_langs:
- C++
helpviewer_keywords:
- _dupenv_s function
- _tdupenv_s function
- _wdupenv_s function
- environment variables
- wdupenv_s function
- dupenv_s function
- tdupenv_s function
ms.assetid: b729ecc2-a31d-4ccf-92a7-5accedb8f8c8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2ec5e7b80d7d3ff2c7f67ec66e4e3e454ea3f5aa
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="dupenvs-wdupenvs"></a>_dupenv_s, _wdupenv_s
Pobiera wartość po bieżącym środowisku.  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _dupenv_s(  
   char **buffer,  
   size_t *numberOfElements,  
   const char *varname  
);  
errno_t _wdupenv_s(  
   wchar_t **buffer,  
   size_t *numberOfElements,  
   const wchar_t *varname  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Bufor do przechowywania wartość zmiennej.  
  
 `numberOfElements`  
 Rozmiar `buffer`.  
  
 `varname`  
 Nazwa zmiennej środowiskowej.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero w przypadku powodzenia, kod błędu w przypadku awarii.  
  
 Te funkcje walidację ich parametrów; Jeśli `buffer` lub `varname` jest `NULL`, zgodnie z opisem w wywołaniu program obsługi nieprawidłowych parametrów [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, Ustaw funkcje `errno` do `EINVAL` i zwracać `EINVAL`.  
  
 Jeśli te funkcje nie może przydzielić wystarczającej ilości pamięci, sami ustawiają `buffer` do `NULL` i `numberOfElements` 0 i powrotu `ENOMEM`.  
  
## <a name="remarks"></a>Uwagi  
 `_dupenv_s` Funkcja wyszukuje listę zmiennych środowiskowych dla `varname`. Jeśli zmienna zostanie znaleziony, `_dupenv_s` przydziela buforu i kopiuje wartość zmiennej w buforze. Adres buforu i długość są zwracane w `buffer` i `numberOfElements`. Przydzielając buforu, `_dupenv_s` wygodniejsze alternatywą dla [getenv_s —, _wgetenv_s —](../../c-runtime-library/reference/getenv-s-wgetenv-s.md).  
  
> [!NOTE]
>  Jest odpowiedzialny za program wywołujący, aby zwolnić pamięć, wywołując [wolnego](../../c-runtime-library/reference/free.md).  
  
 Jeśli zmienna nie zostanie znaleziony, następnie `buffer` ustawiono `NULL`, `numberOfElements` jest ustawiona na 0, i zwracana wartość wynosi 0, ponieważ ta sytuacja nie jest traktowana jako warunek błędu.  
  
 Jeśli nie jesteś zainteresowany rozmiar buforu można przekazać `NULL` dla `numberOfElements`.  
  
 `_dupenv_s` nie jest uwzględniana wielkość liter w systemie operacyjnym Windows. `_dupenv_s` używa kopii środowiska wskazywanej przez zmienną globalne `_environ` można uzyskiwać dostęp do środowiska. Zobacz uwagi w [getenv_s —, _wgetenv_s —](../../c-runtime-library/reference/getenv-s-wgetenv-s.md) omówienie `_environ`.  
  
 Wartość w `buffer` jest kopią wartości zmiennej środowiskowej; modyfikowania jej nie ma wpływu na środowisko. Użyj [_putenv_s —, _wputenv_s —](../../c-runtime-library/reference/putenv-s-wputenv-s.md) funkcji, aby zmodyfikować wartość zmiennej środowiskowej.  
  
 `_wdupenv_s` jest to wersja znaków dwubajtowych `_dupenv_s`; argumentów `_wdupenv_s` są ciągami znaków dwubajtowych. `_wenviron` — Zmienna globalna jest wersja znaków dwubajtowych `_environ`. Zobacz uwagi w [getenv_s —, _wgetenv_s —](../../c-runtime-library/reference/getenv-s-wgetenv-s.md) Aby uzyskać więcej informacji na temat `_wenviron`.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tdupenv_s`|`_dupenv_s`|`_dupenv_s`|`_wdupenv_s`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_dupenv_s`|\<stdlib.h>|  
|`_wdupenv_s`|\<stdlib.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_dupenv_s.c  
#include  <stdlib.h>  
  
int main( void )  
{  
   char *pValue;  
   size_t len;  
   errno_t err = _dupenv_s( &pValue, &len, "pathext" );  
   if ( err ) return -1;  
   printf( "pathext = %s\n", pValue );  
   free( pValue );  
   err = _dupenv_s( &pValue, &len, "nonexistentvariable" );  
   if ( err ) return -1;  
   printf( "nonexistentvariable = %s\n", pValue );  
   free( pValue ); // It's OK to call free with NULL  
}  
```  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl  
nonexistentvariable = (null)  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Proces i kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)   
 [Stałe środowiska](../../c-runtime-library/environmental-constants.md)   
 [_dupenv_s_dbg, _wdupenv_s_dbg](../../c-runtime-library/reference/dupenv-s-dbg-wdupenv-s-dbg.md)   
 [getenv_s, _wgetenv_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md)   
 [_putenv_s, _wputenv_s](../../c-runtime-library/reference/putenv-s-wputenv-s.md)