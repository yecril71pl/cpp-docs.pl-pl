---
title: _fullpath, _wfullpath | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _fullpath
- _wfullpath
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wfullpath
- fullpath
- _wfullpath
- _fullpath
dev_langs:
- C++
helpviewer_keywords:
- _wfullpath function
- relative file paths
- absolute paths
- wfullpath function
- _fullpath function
- fullpath function
ms.assetid: 4161ec17-0d22-45dd-b07d-0222553afae9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a9874d4c0b3576f79880d95a04285be9ff299c7c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="fullpath-wfullpath"></a>_fullpath, _wfullpath
Tworzy ścieżkę bezwzględną lub pełną nazwę określoną ścieżką względną.  
  
## <a name="syntax"></a>Składnia  
  
```  
char *_fullpath(   
   char *absPath,  
   const char *relPath,  
   size_t maxLength   
);  
wchar_t *_wfullpath(   
   wchar_t *absPath,  
   const wchar_t *relPath,  
   size_t maxLength   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `absPath`  
 Wskaźnik do bufor zawierający ścieżkę bezwzględną lub Pełna nazwa lub wartość NULL.  
  
 `relPath`  
 Nazwa ścieżki względnej.  
  
 `maxLength`  
 Maksymalna długość buforu nazwy ścieżkę bezwzględną (`absPath`). Jest to długość w bajtach dla `_fullpath` , ale w znaki dwubajtowe (`wchar_t`) dla `_wfullpath`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda z tych funkcji zwraca wskaźnik do buforu, zawierający nazwę ścieżkę bezwzględną (`absPath`). Jeśli błąd (na przykład, jeśli wartość przekazano `relPath` zawiera literę dysku, który jest nieprawidłowy lub nie można znaleźć, lub jeśli długość nazwy utworzonego ścieżkę bezwzględną (`absPath`) jest większa niż `maxLength`), funkcja zwraca `NULL`.  
  
## <a name="remarks"></a>Uwagi  
 `_fullpath` Funkcja rozszerza nazwy ścieżki względnej w `relPath` ścieżka w pełni kwalifikowaną lub bezwzględną i magazyny to imię i nazwisko `absPath`. Jeśli `absPath` ma wartość NULL, `malloc` służy można przydzielić bufora o długości wystarczające, aby pomieścić nazwę ścieżki. Jest odpowiedzialny za obiekt wywołujący, aby zwolnić tego buforu. Względna ścieżka Określa ścieżkę do innej lokalizacji z bieżącej lokalizacji (takich jak bieżący katalog roboczy: "."). Nazwa ścieżki jest rozszerzenie nazwy ścieżki względnej, stwierdzający całej ścieżki, które są wymagane do uzyskania żądanej lokalizacji z katalogu głównego systemu plików. W odróżnieniu od `_makepath`, `_fullpath` może zostać użyty do uzyskania nazwę ścieżki bezwzględnej ścieżki względne (`relPath`) zawierające ". /"lub".. / "w ich nazwy.  
  
 Na przykład aby użyć procedury środowiska wykonawczego języka C, aplikacja musi zawierać pliki nagłówkowe, zawierające deklaracje dla procedury. Każdy plik nagłówka obejmują instrukcji odwołuje się do lokalizacji pliku w sposób względny (od katalog roboczy aplikacji):  
  
```  
#include <stdlib.h>  
```  
  
 Jeśli ścieżka bezwzględna (rzeczywista lokalizacja systemu plików) w pliku może być:  
  
```  
\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h  
```  
  
 `_fullpath` automatycznie obsługuje argumentów ciągów znaków wielobajtowych zgodnie z potrzebami, rozpoznawanie wielobajtowych sekwencji znaków zgodnie ze strony kodowe wielobajtowe obecnie w użyciu. `_wfullpath` jest to wersja znaków dwubajtowych `_fullpath`; argumenty ciągu `_wfullpath` są ciągami znaków dwubajtowych. `_wfullpath` i `_fullpath` zachowują się tak samo, z wyjątkiem `_wfullpath` nie obsługuje ciągów znaków wielobajtowych.  
  
 Jeśli `_DEBUG` i `_CRTDBG_MAP_ALLOC` są zdefiniowane, wywołania `_fullpath` i `_wfullpath` zastępuje wywołań `_fullpath_dbg` i `_wfullpath_dbg` umożliwiające profilowanie przydziału pamięci. Aby uzyskać więcej informacji, zobacz [_fullpath_dbg —, _wfullpath_dbg —](../../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md).  
  
 Ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md), jeśli `maxlen` jest mniejsza niż lub równa 0. Jeśli wykonanie może kontynuować, ta funkcja ustawia `errno` do `EINVAL` i zwraca `NULL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfullpath`|`_fullpath`|`_fullpath`|`_wfullpath`|  
  
 Jeśli `absPath` bufor jest `NULL`, `_fullpath` wywołania [— funkcja malloc](../../c-runtime-library/reference/malloc.md) alokować buforu ignoruje `maxLength` argumentu. Odpowiedzialność wywołującego można cofnąć alokacji buforu (przy użyciu [wolnego](../../c-runtime-library/reference/free.md)) jako odpowiednie. Jeśli `relPath` argument określa dysk, bieżącego katalogu tego dysku są łączone ze ścieżką.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`_fullpath`|\<stdlib.h>|  
|`_wfullpath`|\<stdlib.h > lub \<wchar.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_fullpath.c  
// This program demonstrates how _fullpath  
// creates a full path from a partial path.  
  
#include <stdio.h>  
#include <conio.h>  
#include <stdlib.h>  
#include <direct.h>  
  
void PrintFullPath( char * partialPath )  
{  
   char full[_MAX_PATH];  
   if( _fullpath( full, partialPath, _MAX_PATH ) != NULL )  
      printf( "Full path is: %s\n", full );  
   else  
      printf( "Invalid path\n" );  
}  
  
int main( void )  
{  
   PrintFullPath( "test" );  
   PrintFullPath( "\\test" );  
   PrintFullPath( "..\\test" );  
}  
```  
  
```Output  
Full path is: C:\Documents and Settings\user\My Documents\test  
Full path is: C:\test  
Full path is: C:\Documents and Settings\user\test  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa plików](../../c-runtime-library/file-handling.md)   
 [_getcwd, _wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [_getdcwd, _wgetdcwd](../../c-runtime-library/reference/getdcwd-wgetdcwd.md)   
 [_makepath —, _wmakepath —](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [_splitpath, _wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)