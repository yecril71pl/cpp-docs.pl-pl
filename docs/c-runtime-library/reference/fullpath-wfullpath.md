---
title: _fullpath, _wfullpath
ms.date: 11/04/2016
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
helpviewer_keywords:
- _wfullpath function
- relative file paths
- absolute paths
- wfullpath function
- _fullpath function
- fullpath function
ms.assetid: 4161ec17-0d22-45dd-b07d-0222553afae9
ms.openlocfilehash: aeacaf581b7f33ee893754c192ae547376ce73ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287645"
---
# <a name="fullpath-wfullpath"></a>_fullpath, _wfullpath

Tworzy ścieżkę bezwzględną, lub pełną nazwę określoną ścieżką względną.

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
Wskaźnik do buforu, zawierające nazwę ścieżki bezwzględnej lub pełnego lub **NULL**.

*relPath*<br/>
Nazwa ścieżki względnej.

*maxLength*<br/>
Maksymalna długość buforu nazwy ścieżkę bezwzględną (*absPath*). To długość jest w bajtach dla **_fullpath —** , ale w znaków dwubajtowych (**wchar_t**) dla **_wfullpath —**.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do buforu, zawierający nazwę ścieżkę bezwzględną (*absPath*). Jeśli wystąpi błąd (na przykład, jeśli wartość przekazywana w *relPath* zawiera literę dysku, który jest nieprawidłowy lub nie można odnaleźć, lub jeśli długość nazwy utworzona ścieżka bezwzględna (*absPath*) jest większa niż *maxLength*), funkcja zwraca **NULL**.

## <a name="remarks"></a>Uwagi

**_Fullpath —** funkcja rozszerza nazwę ścieżki względnej w *relPath* jego w pełni kwalifikowaną lub bezwzględna ścieżka i magazyny to imię i nazwisko *absPath*. Jeśli *absPath* jest **NULL**, **— funkcja malloc** jest używany, można przydzielić bufora wystarczająco długa, aby pomieścić nazwę ścieżki. Jest odpowiedzialny za obiekt wywołujący, aby zwolnić buforu. Nazwa ścieżki względnej Określa ścieżkę do innej lokalizacji z bieżącej lokalizacji (np. bieżący katalog roboczy: "."). Nazwa ścieżki bezwzględnej jest rozszerzenie pełną ścieżkę, wymagane do uzyskania żądanej lokalizacji systemu plików z katalogu głównego, stwierdzający, że nazwa ścieżki względnej. W odróżnieniu od **_makepath —**, **_fullpath —** można uzyskać nazwy ścieżki bezwzględnej dla ścieżek względnych (*relPath*) zawierające ". /"lub".. / "w nazwach.

Na przykład aby użyć procedury czasu wykonywania języka C, aplikacja musi zawierać pliki nagłówkowe, które zawierać deklaracje dla procedur. Każdy plik nagłówkowy obejmują odwołuje się do instrukcji lokalizację pliku w sposób względnych (z katalogu roboczego aplikacji):

```C
#include <stdlib.h>
```

Jeśli ścieżka bezwzględna (rzeczywista lokalizacja systemu plików) plik może być:

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

**_fullpath —** automatycznie obsługuje argumenty ciągu znaków wielobajtowych zgodnie z potrzebami, rozpoznawaniu sekwencje znaków wielobajtowych zgodnie z aktualnie używaną stroną kodową wielobajtowe. **_wfullpath —** to wersja znaku dwubajtowego **_fullpath —**; argumentów ciągów **_wfullpath —** są ciągami znaków dwubajtowych. **_wfullpath —** i **_fullpath —** zachowują się identycznie, chyba że **_wfullpath —** nie obsługuje ciągi znaków wielobajtowych.

Jeśli **_DEBUG** i **_CRTDBG_MAP_ALLOC** są zarówno zdefiniowany, wywołania **_fullpath —** i **_wfullpath —** są zastępowane przez wywołania **_fullpath_dbg —** i **_wfullpath_dbg —** aby umożliwić debugowanie alokacji pamięci. Aby uzyskać więcej informacji, zobacz [_fullpath_dbg —, _wfullpath_dbg —](fullpath-dbg-wfullpath-dbg.md).

Ta funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md), jeśli *maxlen* jest mniejszy niż lub równe 0. Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca **NULL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath**|**_fullpath**|**_wfullpath**|

Jeśli *absPath* bufor jest **NULL**, **_fullpath —** wywołania [— funkcja malloc](malloc.md) można przydzielić bufora i ignoruje *maxLength*  argumentu. Odpowiada za wywołującego można cofnąć alokacji buforu (przy użyciu [bezpłatne](free.md)) odpowiednio. Jeśli *relPath* argument określa dysk, bieżący katalog ten dysk jest w połączeniu ze ścieżką.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_fullpath**|\<stdlib.h>|
|**_wfullpath**|\<stdlib.h> or \<wchar.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
