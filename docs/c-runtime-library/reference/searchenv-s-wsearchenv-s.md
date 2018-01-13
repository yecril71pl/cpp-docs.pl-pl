---
title: "_searchenv_s —, _wsearchenv_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wsearchenv_s
- _searchenv_s
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
- _searchenv_s
- _wsearchenv_s
- wsearchenv_s
- searchenv_s
dev_langs: C++
helpviewer_keywords:
- tsearchenv_s function
- files [C++], finding
- buffers [C++], buffer overruns
- environment paths, searching for files
- wsearchenv_s function
- searchenv_s function
- _tsearchenv_s function
- buffer overruns
- buffers [C++], avoiding overruns
- _wsearchenv_s function
- _searchenv_s function
- environment paths
ms.assetid: 47f9fc29-250e-4c09-b52e-9e9f0ef395ca
caps.latest.revision: "32"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6f1089aa1f772832417168a2262fa72069b3ede7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="searchenvs-wsearchenvs"></a>_searchenv_s, _wsearchenv_s
Wyszukiwanie plików przy użyciu ścieżki środowiska. Te wersje programu [_searchenv —, _wsearchenv —](../../c-runtime-library/reference/searchenv-wsearchenv.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _searchenv_s(  
   const char *filename,  
   const char *varname,  
   char *pathname,  
   size_t numberOfElements  
);  
errno_t _wsearchenv_s(  
   const wchar_t *filename,  
   const wchar_t *varname,  
   wchar_t *pathname,  
   size_t numberOfElements  
);  
template <size_t size>  
errno_t _searchenv_s(  
   const char *filename,  
   const char *varname,  
   char (&pathname)[size]  
); // C++ only  
template <size_t size>  
errno_t _wsearchenv_s(  
   const wchar_t *filename,  
   const wchar_t *varname,  
   wchar_t (&pathname)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`filename`  
 Nazwa pliku do wyszukania.  
  
 [in]`varname`  
 Środowisko wyszukiwania.  
  
 [out]`pathname`  
 Bufor do przechowywania pełną ścieżkę.  
  
 [in]`numberOfElements`  
 Rozmiar `pathname` buforu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero w przypadku powodzenia; błąd o kodzie błędu.  
  
 Jeśli `filename` to ciąg pusty jest zwracana wartość `ENOENT`.  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|`filename`|`varname`|`pathname`|`numberOfElements`|Wartość zwracana|Zawartość`pathname`|  
|----------------|---------------|----------------|------------------------|------------------|----------------------------|  
|wszystkie|wszystkie|`NULL`|wszystkie|`EINVAL`|n/d|  
|`NULL`|wszystkie|wszystkie|wszystkie|`EINVAL`|nie został zmieniony|  
|wszystkie|wszystkie|wszystkie|<= 0|`EINVAL`|nie został zmieniony|  
  
 Jeśli dowolny z tych warunków błąd wystąpi, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL` i zwracać `EINVAL`.  
  
## <a name="remarks"></a>Uwagi  
 `_searchenv_s` Procedura wyszukiwania dla pliku docelowego w określonej domenie. `varname` Zmiennej może być dowolną środowiska lub zmiennej zdefiniowanej przez użytkownika określa listę ścieżki katalogu, takie jak `PATH`, `LIB`, i `INCLUDE`. Ponieważ `_searchenv_s` jest rozróżniana wielkość liter, `varname` powinno być zgodne w przypadku ustawienia zmiennej środowiskowej. Jeśli `varname` nie odpowiada nazwa zmiennej środowiskowej zdefiniowana w środowisku procesu, funkcja zwraca wartość zero i `pathname` zmienna jest bez zmian.  
  
 Procedura najpierw szuka pliku w bieżącym katalogu roboczym. Jeśli plik nie zostanie znaleziona, wygląda dalej za pośrednictwem katalogów, określonej przez zmienną środowiskową. Jeśli plik docelowy znajduje się w jednym z tych katalogów, nowo utworzona ścieżka jest kopiowana do `pathname`. Jeśli `filename` nie znaleziono pliku `pathname` zawiera pusty ciąg zerem.  
  
 `pathname` Buforu powinien być co najmniej `_MAX_PATH` znaków, aby pomieścić długie nazwy ścieżki skonstruowane. W przeciwnym razie `_searchenv_s` może przepełnienie `pathname` buforu spowodować nieoczekiwane zachowanie.  
  
 `_wsearchenv_s`jest to wersja znaków dwubajtowych `_searchenv_s`; argumenty `_wsearchenv_s` są ciągami znaków dwubajtowych. `_wsearchenv_s`i `_searchenv_s` zachowują się tak samo w przeciwnym razie wartość.  
  
 W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (wyeliminowanie konieczności określania argumentem rozmiaru) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje z ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tsearchenv_s`|`_searchenv_s`|`_searchenv_s`|`_wsearchenv_s`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_searchenv_s`|\<stdlib.h >|  
|`_wsearchenv_s`|\<stdlib.h > lub \<wchar.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_searchenv_s.c  
/* This program searches for a file in  
 * a directory specified by an environment variable.  
 */  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char pathbuffer[_MAX_PATH];  
   char searchfile[] = "CL.EXE";  
   char envvar[] = "PATH";  
   errno_t err;  
  
   /* Search for file in PATH environment variable: */  
   err = _searchenv_s( searchfile, envvar, pathbuffer, _MAX_PATH );  
   if (err != 0)  
   {  
      printf("Error searching the path. Error code: %d\n", err);  
   }  
   if( *pathbuffer != '\0' )  
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );  
   else  
      printf( "%s not found\n", searchfile );  
}  
```  
  
```Output  
Path for CL.EXE:  
C:\Program Files\Microsoft Visual Studio 2010\VC\BIN\CL.EXE  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola katalogu](../../c-runtime-library/directory-control.md)   
 [_searchenv —, _wsearchenv —](../../c-runtime-library/reference/searchenv-wsearchenv.md)   
 [getenv —, _wgetenv —](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [_putenv, _wputenv](../../c-runtime-library/reference/putenv-wputenv.md)