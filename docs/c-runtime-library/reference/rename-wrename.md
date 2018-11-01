---
title: rename, _wrename
ms.date: 11/04/2016
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
ms.openlocfilehash: 70793dee54460b6372bfbe815115aa9211670c6f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463989"
---
# <a name="rename-wrename"></a>rename, _wrename

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

*StaraNazwa*<br/>
Wskaźnik do starej nazwy.

*Nowa nazwa*<br/>
Wskaźnik na nową nazwę.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość 0, jeśli to się powiodło. W przypadku błędu, funkcja zwraca wartość różną od zera i ustawia **errno** do jednej z następujących wartości:

|errno wartość|Warunek|
|-|-|
**EACCES**|Pliku lub katalogu określonym przez *newname* już istnieje albo nie można utworzyć (Nieprawidłowa ścieżka); lub *StaraNazwa* jest katalogiem i *newname* Określa inną ścieżkę.
**ENOENT**|Plik lub ścieżka określona przez plik *StaraNazwa* nie można odnaleźć.
**EINVAL**|Nazwa zawiera nieprawidłowe znaki.

Dla innych możliwych wartości zwracanych [_doserrno, _errno, syserrlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**Zmień nazwę** funkcja zmienia nazwę pliku lub katalogu określonym przez *StaraNazwa* nazwa podana przez *newname*. Stara nazwa musi być ścieżka istniejącego pliku lub katalogu. Nowa nazwa nie musi być nazwa istniejącego pliku lub katalogu. Możesz użyć **Zmień nazwę** można przenieść pliku z jednego katalogu lub urządzenia do innego, zapewniając inną ścieżkę *newname* argumentu. Nie można jednak użyć **Zmień nazwę** można przenieść katalogu. Katalogi można zmienić nazwy, ale nie przenieść.

**_wrename —** to wersja znaku dwubajtowego **_rename**; argumenty **_wrename —** są ciągami znaków dwubajtowych. **_wrename —** i **_rename** zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_trename —**|**Zmień nazwę**|**Zmień nazwę**|**_wrename —**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Zmień nazwę**|\<IO.h > lub \<stdio.h >|
|**_wrename —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
