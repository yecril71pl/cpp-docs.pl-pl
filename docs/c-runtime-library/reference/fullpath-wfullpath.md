---
title: _fullpath, _wfullpath
ms.date: 11/04/2016
api_name:
- _fullpath
- _wfullpath
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wfullpath
- fullpath
- _wfullpath
- _fullpath
helpviewer_keywords:
- _wfullpath function
- relative file paths
- absolute paths
- wfullpath function
- _fullpath function
- fullpath function
ms.assetid: 4161ec17-0d22-45dd-b07d-0222553afae9
ms.openlocfilehash: 30e62716c496ebb1a39b53a420f372a6e743c2c0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956268"
---
# <a name="_fullpath-_wfullpath"></a>_fullpath, _wfullpath

Tworzy bezwzględną lub pełną nazwę ścieżki dla określonej nazwy ścieżki względnej.

## <a name="syntax"></a>Składnia

```C
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

### <a name="parameters"></a>Parametry

*absPath*<br/>
Wskaźnik do buforu zawierającego bezwzględną lub pełną nazwę ścieżki lub **wartość null**.

*relPath*<br/>
Nazwa ścieżki względnej.

*maxLength*<br/>
Maksymalna długość buforu nazw ścieżek bezwzględnych (*absPath*). Ta długość jest wyrażona w bajtach dla **_fullpath** , ale w postaci szerokich znaków (**wchar_t**) dla **_wfullpath**.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do buforu zawierającego bezwzględną nazwę ścieżki (*absPath*). Jeśli wystąpi błąd (na przykład, jeśli wartość przeniesiona w *relPath* zawiera literę dysku, która jest nieprawidłowa lub nie można jej znaleźć lub jeśli długość utworzonej ścieżki bezwzględnej (*absPath*) jest większa niż *MaxLength*), funkcja zwraca **Wartość null**.

## <a name="remarks"></a>Uwagi

Funkcja **_fullpath** rozszerza względną nazwę ścieżki w *relPath* na jej w pełni kwalifikowaną lub bezwzględną ścieżkę i zapisuje tę nazwę w *absPath*. Jeśli *absPath* ma **wartość null**, **malloc** służy do przydzielenia bufora o wystarczającej długości, aby pomieścić nazwę ścieżki. Obiekt wywołujący jest odpowiedzialny za zwolnienie tego buforu. Nazwa ścieżki względnej określa ścieżkę do innej lokalizacji z bieżącej lokalizacji (na przykład bieżący katalog roboczy: "."). Ścieżka bezwzględna jest rozszerzeniem nazwy ścieżki względnej, która określa, że cała ścieżka jest wymagana do osiągnięcia żądanej lokalizacji z katalogu głównego systemu plików. W przeciwieństwie do **_makepath**, **_fullpath** może służyć do uzyskania nazwy ścieżki bezwzględnej dla ścieżek względnych (*relPath*), które zawierają "./" lub ".. /".

Na przykład, aby użyć procedur czasu wykonywania języka C, aplikacja musi zawierać pliki nagłówkowe zawierające deklaracje dla procedur. Każda instrukcja include pliku nagłówkowego odwołuje się do lokalizacji pliku w sposób względny (z katalogu roboczego aplikacji):

```C
#include <stdlib.h>
```

ścieżka bezwzględna (Rzeczywista lokalizacja systemu plików) pliku może być:

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

**_fullpath** automatycznie obsługuje argumenty ciągu znaków wielobajtowych, aby rozpoznać sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową. **_wfullpath** to dwubajtowa wersja **_fullpath**; argumenty ciągu do **_wfullpath** są ciągami znaków dwubajtowych. **_wfullpath** i **_fullpath** zachowują się identycznie, z tą różnicą, że **_wfullpath** nie obsługują ciągów znaków wielobajtowych.

Jeśli **_DEBUG** i **_CRTDBG_MAP_ALLOC** są zdefiniowane, wywołania do **_fullpath** i **_wfullpath** są zastępowane wywołaniami **_fullpath_dbg** i **_wfullpath_dbg** , aby umożliwić debugowanie alokacji pamięci. Aby uzyskać więcej informacji, zobacz [_fullpath_dbg, _wfullpath_dbg](fullpath-dbg-wfullpath-dbg.md).

Ta funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md), jeśli wartość *MaxLen* jest mniejsza lub równa 0. Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca **wartość null**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath**|**_fullpath**|**_wfullpath**|

Jeśli bufor *absPath* ma **wartość null**, **_fullpath** wywołuje metodę [malloc](malloc.md) w celu przydzielenia buforu i ignoruje argument *MaxLength* . Jest on odpowiedzialny za przydzielenie tego buforu ( [bezpłatnie](free.md)) zgodnie z potrzebami. Jeśli argument *relPath* określa dysk, bieżący katalog tego dysku zostanie połączony ze ścieżką.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fullpath**|\<stdlib.h>|
|**_wfullpath**|\<STDLIB. h > lub \<WCHAR. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
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

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
