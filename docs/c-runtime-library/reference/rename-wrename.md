---
title: "Zmień nazwę _wrename — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- rename
- _wrename
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
- _wrename
- _trename
- Rename
dev_langs: C++
helpviewer_keywords:
- trename function
- directories [C++], renaming
- renaming directories
- names [C++], changing file
- _trename function
- rename function
- wrename function
- files [C++], renaming
- _wrename function
- names [C++], changing directory
- renaming files
ms.assetid: 9f0a6103-26a2-4dda-b14b-79a48946266a
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e26ebd870d30e61b06aff1f7c13298883c99aae5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="rename-wrename"></a>rename, _wrename
Zmień nazwę pliku lub katalogu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      int rename(  
   const char *oldname,  
   const char *newname   
);  
int _wrename(  
   const wchar_t *oldname,  
   const wchar_t *newname   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *StaraNazwa*  
 Wskaźnik do starej nazwy.  
  
 *Nowa nazwa*  
 Wskaźnik na nową nazwę.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda z tych funkcji zwraca wartość 0, jeśli powiedzie się. W przypadku wystąpienia błędu, funkcja zwraca wartość różną od zera i ustawia `errno` do jednej z następujących wartości:  
  
 `EACCES`  
 Plik lub katalog określony przez *newname* już nie istnieje lub nie można utworzyć (Nieprawidłowa ścieżka); lub *StaraNazwa* jest katalogiem i *newname* Określa inną ścieżkę.  
  
 `ENOENT`  
 Plik lub ścieżka określona przez *StaraNazwa* nie można odnaleźć.  
  
 `EINVAL`  
 Nazwa zawiera nieprawidłowe znaki.  
  
 Dla innych możliwych wartości zwrotnych, zobacz [_doserrno —, _errno, syserrlist i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 **Zmienić** funkcja zmienia nazwę pliku lub katalogu określonego przez *StaraNazwa* nazwy podanej przez *newname*. Stara nazwa musi być ścieżka istniejącego pliku lub katalogu. Nowa nazwa nie może być nazwą pliku lub katalogu. Można użyć **zmienić** można przenieść pliku z jednego katalogu lub urządzenia do innego, zapewniając inną ścieżkę *newname* argumentu. Nie można jednak użyć **zmienić** można przenieść katalogu. Katalogi można zmienić nazwy, ale nie została przeniesiona.  
  
 `_wrename`jest to wersja znaków dwubajtowych **_rename**; argumenty `_wrename` są ciągami znaków dwubajtowych. `_wrename`i **_rename** zachowują się tak samo w przeciwnym razie wartość.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_trename`|**Zmień nazwę**|**Zmień nazwę**|`_wrename`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|**Zmień nazwę**|\<IO.h > lub \<stdio.h >|  
|`_wrename`|\<stdio.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_renamer.c  
/* This program attempts to rename a file named  
 * CRT_RENAMER.OBJ to CRT_RENAMER.JBO. For this operation  
 * to succeed, a file named CRT_RENAMER.OBJ must exist and  
 * a file named CRT_RENAMER.JBO must not exist.  
 */  
  
#include <stdio.h>  
  
int main( void )  
{  
   int  result;  
   char old[] = "CRT_RENAMER.OBJ", new[] = "CRT_RENAMER.JBO";  
  
   /* Attempt to rename file: */  
   result = rename( old, new );  
   if( result != 0 )  
      printf( "Could not rename '%s'\n", old );  
   else  
      printf( "File '%s' renamed to '%s'\n", old, new );  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
File 'CRT_RENAMER.OBJ' renamed to 'CRT_RENAMER.JBO'  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa plików](../../c-runtime-library/file-handling.md)