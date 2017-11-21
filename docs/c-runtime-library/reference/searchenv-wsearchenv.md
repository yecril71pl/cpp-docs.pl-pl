---
title: "_searchenv —, _wsearchenv — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _searchenv
- _wsearchenv
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
- _wsearchenv
- _tsearchenv
- wsearchenv
- _searchenv
- searchenv
dev_langs: C++
helpviewer_keywords:
- _wsearchenv function
- files [C++], finding
- _searchenv function
- tsearchenv function
- environment paths, searching for files
- _tsearchenv function
- wsearchenv function
- searchenv function
- environment paths
ms.assetid: 9c944a27-d326-409b-aee6-410e8762d9d3
caps.latest.revision: "33"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 553d51363479a220b5850af2a7ff3ad880c31878
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="searchenv-wsearchenv"></a>_searchenv, _wsearchenv
Używa środowiska ścieżek, aby wyszukać plik. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_searchenv_s —, _wsearchenv_s —](../../c-runtime-library/reference/searchenv-s-wsearchenv-s.md).  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
void _searchenv(  
   const char *filename,  
   const char *varname,  
   char *pathname   
);  
void _wsearchenv(  
   const wchar_t *filename,  
   const wchar_t *varname,  
   wchar_t *pathname   
);  
template <size_t size>  
void _searchenv(  
   const char *filename,  
   const char *varname,  
   char (&pathname)[size]  
); // C++ only  
template <size_t size>  
void _wsearchenv(  
   const wchar_t *filename,  
   const wchar_t *varname,  
   wchar_t (&pathname)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Nazwa pliku do wyszukania.  
  
 `varname`  
 Środowisko wyszukiwania.  
  
 `pathname`  
 Bufor do przechowywania pełną ścieżkę.  
  
## <a name="remarks"></a>Uwagi  
 `_searchenv` Procedura wyszukiwania dla pliku docelowego w określonej domenie. `varname` Zmiennej może być dowolną środowiska lub zmiennej zdefiniowanej przez użytkownika — na przykład `PATH`, `LIB`, lub `INCLUDE`—, który określa listę ścieżki katalogu. Ponieważ `_searchenv` jest rozróżniana wielkość liter, `varname` powinno być zgodne w przypadku ustawienia zmiennej środowiskowej.  
  
 Procedura najpierw szuka pliku w bieżącym katalogu roboczym. Jeśli plik nie zostanie znaleziona, przeszukiwanie katalogi, które są określone przez zmienną środowiskową. Jeśli plik docelowy znajduje się w jednym z tych katalogów, nowo utworzona ścieżka jest kopiowana do `pathname`. Jeśli `filename` nie znaleziono pliku `pathname` zawiera pusty ciąg zerem.  
  
 `pathname` Buforu powinien być co najmniej `_MAX_PATH` znaków, aby pomieścić długie nazwy ścieżki skonstruowane. W przeciwnym razie `_searchenv` może przepełnienie `pathname` buforu i spowodować nieoczekiwane zachowanie.  
  
 `_wsearchenv`jest to wersja znaków dwubajtowych `_searchenv`i argumenty `_wsearchenv` są ciągami znaków dwubajtowych. `_wsearchenv`i `_searchenv` zachowują się tak samo w przeciwnym razie wartość.  
  
 Jeśli `filename` jest pustym ciągiem, te funkcje zwracają `ENOENT`.  
  
 Jeśli `filename` lub `pathname` jest `NULL` wskaźnika, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli wykonanie może kontynuować, następujące funkcje i ustaw `errno` do `EINVAL`.  
  
 Aby uzyskać więcej informacji na temat `errno` i kody błędów, zobacz [errno — stałe](../../c-runtime-library/errno-constants.md).  
  
 W języku C++ tych funkcji mają przeciążenia szablonu, które wywołują odpowiedników nowsze, bezpieczniejsze tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tsearchenv`|`_searchenv`|`_searchenv`|`_wsearchenv`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_searchenv`|\<stdlib.h >|  
|`_wsearchenv`|\<stdlib.h > lub \<wchar.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```C  
// crt_searchenv.c  
// compile with: /W3  
// This program searches for a file in  
// a directory that's specified by an environment variable.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char pathbuffer[_MAX_PATH];  
   char searchfile[] = "CL.EXE";  
   char envvar[] = "PATH";  
  
   // Search for file in PATH environment variable:  
   _searchenv( searchfile, envvar, pathbuffer ); // C4996  
   // Note: _searchenv is deprecated; consider using _searchenv_s  
   if( *pathbuffer != '\0' )  
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );  
   else  
      printf( "%s not found\n", searchfile );  
}  
```  
  
```Output  
Path for CL.EXE:  
C:\Program Files\Microsoft Visual Studio 8\VC\BIN\CL.EXE  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola katalogu](../../c-runtime-library/directory-control.md)   
 [getenv —, _wgetenv —](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [_putenv —, _wputenv —](../../c-runtime-library/reference/putenv-wputenv.md)   
 [_searchenv_s —, _wsearchenv_s —](../../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)