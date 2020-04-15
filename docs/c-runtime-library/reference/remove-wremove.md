---
title: remove, _wremove
ms.date: 4/2/2020
api_name:
- _wremove
- remove
- _o__wremove
- _o_remove
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
- remove
- _wremove
- _tremove
helpviewer_keywords:
- tremove function
- _wremove function
- files [C++], deleting
- _tremove function
- files [C++], removing
- wremove function
- remove function
ms.assetid: b6345ec3-3289-4645-93a4-28b9e478cc19
ms.openlocfilehash: 6a3d7ea81b2f6b1a7e87c706ca883394e02dff3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338151"
---
# <a name="remove-_wremove"></a>remove, _wremove

Usuwanie pliku.

## <a name="syntax"></a>Składnia

```C
int remove(
   const char *path
);
int _wremove(
   const wchar_t *path
);
```

### <a name="parameters"></a>Parametry

*Ścieżka*<br/>
Ścieżka pliku do usunięcia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość 0, jeśli plik został pomyślnie usunięty. W przeciwnym razie zwraca wartość -1 i ustawia **errno** albo do **EACCES,** aby wskazać, że ścieżka określa plik tylko do odczytu, określa katalog lub plik jest otwarty, lub **ENOENT,** aby wskazać, że nazwa pliku lub ścieżka nie została znaleziona.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr,](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych.

## <a name="remarks"></a>Uwagi

Funkcja **usuwania** usuwa plik określony przez *ścieżkę.* **_wremove** jest szerokoznakową wersją **_remove**; argument *path* do **_wremove** jest ciągiem znaków o szerokim charakterze. **_wremove** i **_remove** zachowują się identycznie w przeciwnym razie. Wszystkie dojścia do pliku muszą zostać zamknięte, zanim będzie można go usunąć.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tremove**|**remove**|**remove**|**_wremove**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**remove**|\<stdio.h> lub \<io.h>|
|**_wremove**|\<stdio.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_remove.c
/* This program uses remove to delete crt_remove.txt */

#include <stdio.h>

int main( void )
{
   if( remove( "crt_remove.txt" ) == -1 )
      perror( "Could not delete 'CRT_REMOVE.TXT'" );
   else
      printf( "Deleted 'CRT_REMOVE.TXT'\n" );
}
```

### <a name="input-crt_removetxt"></a>Dane wejściowe: crt_remove.txt

```Input
This file will be deleted.
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
Deleted 'CRT_REMOVE.TXT'
```

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_unlink, _wunlink](unlink-wunlink.md)<br/>
