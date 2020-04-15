---
title: _fullpath, _wfullpath
ms.date: 4/2/2020
api_name:
- _fullpath
- _wfullpath
- _o__fullpath
- _o__wfullpath
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
ms.openlocfilehash: 0910cf4f39e00be84e683cd6f3b9afbeb3f2a749
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345485"
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

*absPath (absPath)*<br/>
Wskaźnik do buforu zawierającego nazwę bezwzględną lub pełną ścieżkę lub **NULL**.

*Ścieżka relPath*<br/>
Nazwa ścieżki względnej.

*Maxlength*<br/>
Maksymalna długość buforu nazw ścieżki bezwzględnej (*absPath*). Długość ta jest w bajtach dla **_fullpath** ale w postaci szerokich **(wchar_t)** dla **_wfullpath**.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do buforu zawierającego nazwę ścieżki bezwzględnej (*absPath*). Jeśli występuje błąd (na przykład jeśli wartość przekazana w *relPath* zawiera literę dysku, która jest nieprawidłowa lub nie można odnaleźć lub jeśli długość utworzonej nazwy ścieżki bezwzględnej (*absPath*) jest większa niż *maxLength),* funkcja zwraca **wartość NULL**.

## <a name="remarks"></a>Uwagi

Funkcja **_fullpath** rozszerza nazwę ścieżki względnej w *relPath* do jej w pełni kwalifikowanej lub bezwzględnej ścieżki i przechowuje tę nazwę w *absPath*. Jeśli *absPath* ma **wartość NULL**, **malloc** jest używany do przydzielenia buforu o wystarczającej długości, aby pomieścić nazwę ścieżki. Jest odpowiedzialny za wywołującego, aby zwolnić ten bufor. Nazwa ścieżki względnej określa ścieżkę do innej lokalizacji z bieżącej lokalizacji (na przykład bieżącego katalogu roboczego: "."). Nazwa ścieżki bezwzględnej to rozszerzenie nazwy ścieżki względnej, która określa całą ścieżkę wymaganą do osiągnięcia żądanej lokalizacji z katalogu głównego systemu plików. W przeciwieństwie do **_makepath** **_fullpath** może służyć do uzyskania nazwy ścieżki bezwzględnej dla ścieżek względnych (*relPath*), które zawierają "./" lub ".. /" w ich nazwach.

Na przykład, aby użyć procedur wykonywania języka C, aplikacja musi zawierać pliki nagłówka, które zawierają deklaracje dla procedur. Każdy plik nagłówka zawiera instrukcję odwołuje się do lokalizacji pliku w sposób względny (z katalogu roboczego aplikacji):

```C
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#include <stdlib.h>
```

gdy ścieżka bezwzględna (rzeczywista lokalizacja systemu plików) pliku może być:

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

**_fullpath** automatycznie obsługuje argumenty ciągów wielobajtowych, rozpoznając sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową wielobajtową. **_wfullpath** jest szerokoznakową wersją **_fullpath**; argumenty ciągu do **_wfullpath** są ciągami znaków o szerokich znakach. **_wfullpath** i **_fullpath** zachowywać się identycznie, z tą różnicą, że **_wfullpath** nie obsługuje ciągów znaków wielobajtowych.

Jeśli **zdefiniowano zarówno _DEBUG,** jak i **_CRTDBG_MAP_ALLOC,** wywołania **_fullpath** i **_wfullpath** są zastępowane wywołaniami **_fullpath_dbg** i **_wfullpath_dbg,** aby umożliwić debugowanie alokacji pamięci. Aby uzyskać więcej informacji, zobacz [_fullpath_dbg, _wfullpath_dbg](fullpath-dbg-wfullpath-dbg.md).

Ta funkcja wywołuje nieprawidłowy program obsługi parametrów, zgodnie z opisem w [sprawdzanie poprawności parametrów,](../../c-runtime-library/parameter-validation.md)jeśli *maxlen* jest mniejszy lub równy 0. Jeśli wykonanie jest dozwolone, ta funkcja ustawia **errno** na **Wartość EINVAL** i zwraca **wartość NULL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath**|**_fullpath**|**_wfullpath**|

Jeśli bufor *absPath* ma **wartość NULL**, **_fullpath** wywoła [malloc,](malloc.md) aby przydzielić bufor i ignoruje argument *maxLength.* Jest to odpowiedzialność wywołującego do deallocate tego buforu (przy użyciu [wolnych)](free.md)w stosownych przypadkach. Jeśli argument *relPath* określa dysk, bieżący katalog tego dysku jest łączony ze ścieżką.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fullpath**|\<>|
|**_wfullpath**|\<> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
