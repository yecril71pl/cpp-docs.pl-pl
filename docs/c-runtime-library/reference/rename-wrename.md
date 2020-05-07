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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: b0a5f43d92d6dd85626f00bf5c2a6350e5bfa10f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917800"
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

*StaraNazwa*<br/>
Wskaźnik do starej nazwy.

*Nowa nazwa*<br/>
Wskaźnik na nową nazwę.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość 0, jeśli zakończy się pomyślnie. W przypadku błędu funkcja zwraca wartość różną od zera i ustawia **errno** na jedną z następujących wartości:

|errno wartość|Warunek|
|-|-|
| **EACCES** | Plik lub katalog określony przez *nowa_nazwa* już istnieje lub nie można go utworzyć (nieprawidłowa ścieżka); lub *StaraNazwa* jest katalogiem, a *newname* określa inną ścieżkę. |
| **ENOENT** | Nie znaleziono pliku lub ścieżki określonego przez *StaraNazwa* . |
| **EINVAL** | Nazwa zawiera nieprawidłowe znaki. |

Aby uzyskać inne możliwe wartości zwracane, zobacz [_doserrno, _errno, syserrlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **zmiany** nazwy zmienia nazwę pliku lub katalogu określonego przez *StaraNazwa* na nazwę określoną przez *nowa_nazwa*. Stara nazwa musi być ścieżką istniejącego pliku lub katalogu. Nowa nazwa nie może być nazwą istniejącego pliku lub katalogu. Za pomocą **zmiany nazwy** można przenieść plik z jednego katalogu lub urządzenia do innego, podając inną ścieżkę w argumencie *nowa_nazwa* . Nie można jednak użyć **nazwy** do przeniesienia katalogu. Nazwy katalogów można zmienić, ale nie zostały przeniesione.

**_wrename** to dwubajtowa wersja **_rename**; argumenty do **_wrename** są ciągami znaków dwubajtowych. **_wrename** i **_rename** zachowują się identycznie w inny sposób.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_trename**|**ZmieńNazwę**|**ZmieńNazwę**|**_wrename**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**ZmieńNazwę**|\<IO. h> lub \<stdio. h>|
|**_wrename**|\<stdio. h> lub \<WCHAR. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

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
