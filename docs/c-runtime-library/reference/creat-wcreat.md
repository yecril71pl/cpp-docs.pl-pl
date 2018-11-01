---
title: _creat, _wcreat
ms.date: 11/04/2016
apiname:
- _creat
- _wcreat
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wcreat
- _wcreat
- _creat
- tcreat
- _tcreat
helpviewer_keywords:
- wcreat function
- _wcreat function
- files [C++], creating
- _creat function
- tcreat function
- creat function
- _tcreat function
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
ms.openlocfilehash: 901a95a6a9361f95f38749dacf1a5001d97b3761
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494994"
---
# <a name="creat-wcreat"></a>_creat, _wcreat

Tworzy nowy plik. **_creat —** i **_wcreat —** są przestarzałe; użyj [_sopen_s —, _wsopen_s —](sopen-s-wsopen-s.md) zamiast tego.

## <a name="syntax"></a>Składnia

```C
int _creat(
   const char *filename,
   int pmode
);
int _wcreat(
   const wchar_t *filename,
   int pmode
);
```

### <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Nazwa nowego pliku.

*pmode*<br/>
Ustawienie uprawnienia.

## <a name="return-value"></a>Wartość zwracana

Tych funkcji, jeśli to się powiedzie, przywrócenie deskryptora pliku utworzonego pliku. W przeciwnym wypadku te funkcje zwracają wartość -1 i ustaw **errno** jak pokazano w poniższej tabeli.

|**errno** ustawienie|Opis|
|---------------------|-----------------|
|**EACCES**|*Nazwa pliku* Określa istniejący plik tylko do odczytu lub określa katalog, a nie plikiem.|
|**EMFILE**|Więcej deskryptorów plików nie są dostępne.|
|**ENOENT**|Nie można odnaleźć określonego pliku.|

Jeśli *filename* jest **NULL**, funkcje te wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają wartość -1.

Aby uzyskać więcej informacji na temat tych i innych kodach powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Creat —** — funkcja lub tworzy nowy plik zostanie otwarty i obcina istniejącą grupę. **_wcreat —** to wersja znaku dwubajtowego **_creat —**; *filename* argument **_wcreat —** jest ciągiem znaku dwubajtowego. **_wcreat —** i **_creat —** zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat —**|**_creat**|**_creat**|**_wcreat**|

Jeśli plik określony przez *filename* nie istnieje, nowy plik zostanie utworzony przy użyciu ustawienia dane uprawnienie i jest otwarty do zapisu. Jeśli plik już istnieje, a jego ustawienie uprawnienia umożliwia zapisywanie, **_creat —** obcina pliku długość 0, niszczenie poprzednią zawartość i otwiera go do zapisu. Ustawienie uprawnienia *pmode*, dotyczy tylko dla nowo tworzonych plików. Nowy plik odbiera ustawienia określone uprawnienie jest zamknięte po raz pierwszy. Wyrażenia typu całkowitego *pmode* zawiera jeden lub oba stałe manifestu **_S_IWRITE** i **_S_IREAD**zdefiniowaną w SYS\Stat.h. Gdy oba stałe są podane, są połączone przy użyciu bitowego operatora or — operator ( **&#124;** ). *Pmode* parametr jest ustawiony na jedną z następujących wartości.

|Wartość|Definicja|
|-----------|----------------|
|**_S_IWRITE**|Zapisywanie jest dozwolone.|
|**_S_IREAD**|Odczytywanie dozwolone.|
|**_S_IREAD** &AMP;#124; **_S_IWRITE**|Odczyt i zapis dozwolone.|

Jeśli uprawnienia do zapisu nie zostanie określony, plik jest tylko do odczytu. Wszystkie pliki są zawsze czytelny; nie jest możliwe przyznać uprawnienia tylko do zapisu. Tryby **_S_IWRITE** i **_S_IREAD** | **_S_IWRITE** następnie są równoważne. Pliki otwierane przy użyciu **_creat —** zawsze są otwarte w trybie zgodności (zobacz [_sopen](sopen-wsopen.md)) za pomocą **_SH_DENYNO**.

**_creat —** stosuje bieżące maskę uprawnień do pliku, aby *pmode* przed ustawieniem uprawnienia (zobacz [_umask —](umask.md)). **_creat —** głównie w celu zachowania zgodności z poprzedniej biblioteki. Wywołanie **_otwórz** z **_O_CREAT** i **_O_TRUNC** w *oflag* parametr jest równoważny **_creat —** i jest preferowane dla nowego kodu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_creat**|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wcreat**|\<IO.h > lub \<wchar.h >|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_creat.c
// compile with: /W3
// This program uses _creat to create
// the file (or truncate the existing file)
// named data and open it for writing.

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int fh;

   fh = _creat( "data", _S_IREAD | _S_IWRITE ); // C4996
   // Note: _creat is deprecated; use _sopen_s instead
   if( fh == -1 )
      perror( "Couldn't create data file" );
   else
   {
      printf( "Created data file.\n" );
      _close( fh );
   }
}
```

```Output
Created data file.
```

## <a name="see-also"></a>Zobacz także

[Niskiego poziomu operacji We/Wy](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>
