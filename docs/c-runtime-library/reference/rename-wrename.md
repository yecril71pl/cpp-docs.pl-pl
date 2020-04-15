---
title: rename, _wrename
ms.date: 4/2/2020
api_name:
- rename
- _wrename
- _o__wrename
- _o_rename
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wrename
- _trename
- Rename
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
ms.openlocfilehash: 730458c5027f8f690e8238b29cbdb1056f09ed68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338107"
---
# <a name="rename-_wrename"></a>rename, _wrename

Zmień nazwę pliku lub katalogu.

## <a name="syntax"></a>Składnia

```C
int rename(
   const char *oldname,
   const char *newname
);
int _wrename(
   const wchar_t *oldname,
   const wchar_t *newname
);
```

### <a name="parameters"></a>Parametry

*nazwa staruszka*<br/>
Wskaźnik do starej nazwy.

*Nowa nazwa*<br/>
Wskaźnik do nowej nazwy.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość 0, jeśli zakończy się pomyślnie. W przypadku błędu funkcja zwraca wartość niezerową i ustawia **errno** na jedną z następujących wartości:

|wartość errno|Warunek|
|-|-|
| **EACCES ( EACCES )** | Plik lub katalog określony przez *newname* już istnieje lub nie można go utworzyć (nieprawidłowa ścieżka); lub *oldname* jest katalogiem, a *nowa nazwa* określa inną ścieżkę. |
| **Enoent** | Nie znaleziono pliku lub ścieżki określonej przez *nazwę starą.* |
| **Einval** | Nazwa zawiera nieprawidłowe znaki. |

Aby uzyskać inne możliwe wartości [zwrotu, zobacz _doserrno, _errno, syserrlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **zmiany nazwy** zmienia nazwę pliku lub katalogu określonego przez *starą nazwę* na nazwę nadaną przez *newname*. Stara nazwa musi być ścieżką istniejącego pliku lub katalogu. Nowa nazwa nie może być nazwą istniejącego pliku lub katalogu. Można użyć **zmień nazwę,** aby przenieść plik z jednego katalogu lub urządzenia do innego, nadając inną ścieżkę w argurze *newname.* Nie można jednak użyć **nazwy do** przeniesienia katalogu. Nazwy katalogów można zmienić, ale nie zostały przeniesione.

**_wrename** jest szerokoznakową wersją **_rename**; argumenty, które **mają _wrename,** to ciągi znaków o szerokich znakach. **_wrename** i **_rename** zachowują się identycznie w przeciwnym razie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_trename**|**Zmienić nazwę**|**Zmienić nazwę**|**_wrename**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Zmienić nazwę**|\<io.h> lub \<stdio.h>|
|**_wrename**|\<stdio.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
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

### <a name="output"></a>Dane wyjściowe

```Output
File 'CRT_RENAMER.OBJ' renamed to 'CRT_RENAMER.JBO'
```

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
