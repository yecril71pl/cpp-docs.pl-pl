---
title: _creat, _wcreat
ms.date: 11/04/2016
api_name:
- _creat
- _wcreat
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: d278bffbfdf856956a20b01da4dad2ba00952359
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938890"
---
# <a name="_creat-_wcreat"></a>_creat, _wcreat

Tworzy nowy plik. **_creat** i **_wcreat** są przestarzałe; Zamiast tego użyj [_sopen_s, _wsopen_s](sopen-s-wsopen-s.md) .

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
Ustawienie uprawnień.

## <a name="return-value"></a>Wartość zwracana

Te funkcje, jeśli pomyślnie, zwracają deskryptor pliku do utworzonego pliku. W przeciwnym razie funkcje zwracają-1 i ustawiają **errno** , jak pokazano w poniższej tabeli.

|ustawienie **errno**|Opis|
|---------------------|-----------------|
|**EACCES**|*Nazwa pliku* określa istniejący plik tylko do odczytu lub określa katalog, a nie plik.|
|**EMFILE**|Nie ma więcej dostępnych deskryptorów plików.|
|**ENOENT**|Nie można znaleźć określonego pliku.|

Jeśli *Nazwa pliku* ma **wartość null**, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EINVAL** i Return-1.

Aby uzyskać więcej informacji na temat tych i innych kodów powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_creat** tworzy nowy plik lub otwiera i obcina istniejący. **_wcreat** to dwubajtowa wersja **_creat**; argumentem *filename* **_wcreat** jest ciąg znaków dwubajtowych. **_wcreat** i **_creat** zachowują się identycznie w inny sposób.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

Jeśli plik określony przez *filename* nie istnieje, zostanie utworzony nowy plik z danym ustawieniem uprawnień i zostanie on otwarty do zapisu. Jeśli plik już istnieje, a jego ustawienie uprawnień Zezwalaj na zapisywanie, **_creat** obcina plik do długości 0, niszczy poprzednią zawartość i otwiera go do zapisu. Ustawienie uprawnienia *PMODE*ma zastosowanie tylko do nowo utworzonych plików. Nowy plik otrzymuje określone ustawienie uprawnienia po jego pierwszym zamknięciu. Wyrażenie Integer *PMODE* zawiera jedną lub obie stałe manifestu **_S_IWRITE** i **_S_IREAD**, zdefiniowane w SYS\Stat.h. Po otrzymaniu obu stałych są one przyłączone do operatora bitowego or ( **&#124;** ). Parametr *PMODE* jest ustawiony na jedną z następujących wartości.

|Wartość|Definicja|
|-----------|----------------|
|**_S_IWRITE**|Dozwolone jest zapisanie.|
|**_S_IREAD**|Odczytywanie dozwolone.|
|**_S_IREAD** &#124; **_S_IWRITE**|Dozwolone odczytywanie i zapisywanie.|

Jeśli nie podano uprawnienia do zapisu, plik jest tylko do odczytu. Wszystkie pliki są zawsze do odczytu; nie można przyznać uprawnień tylko do zapisu. Tryby **_S_IWRITE** i **_S_IREAD** |  **_S_IWRITE** są następnie równoważne. Pliki otwarte przy użyciu **_creat** są zawsze otwierane w trybie zgodności (zobacz [_Sopen](sopen-wsopen.md)) z **_SH_DENYNO**.

**_creat** stosuje bieżącą maskę uprawnień pliku do *PMODE* przed ustawieniem uprawnień (zobacz [_umask](umask.md)). **_creat** jest dostarczany głównie w celu zapewnienia zgodności z poprzednimi bibliotekami. Wywołanie **_open** z **_O_CREAT** i **_O_TRUNC** w parametrze *Oflag* jest równoważne z **_creat** i jest preferowane dla nowego kodu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_creat**|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wcreat**|\<IO. h > lub \<WCHAR. h >|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

[We/wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>
