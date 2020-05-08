---
title: _creat, _wcreat
ms.date: 4/2/2020
api_name:
- _creat
- _wcreat
- _o__creat
- _o__wcreat
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 379a4adbf17755341fed6a48c649afe29e150fe5
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912114"
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

Funkcja **_creat** tworzy nowy plik lub otwiera i obcina istniejący. **_wcreat** to dwubajtowa wersja **_creat**; argument *filename* **_wcreat** jest ciągiem znaków dwubajtowych. **_wcreat** i **_creat** zachowują się identycznie w inny sposób.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

Jeśli plik określony przez *filename* nie istnieje, zostanie utworzony nowy plik z danym ustawieniem uprawnień i zostanie on otwarty do zapisu. Jeśli plik już istnieje, a jego uprawnienia zezwalają na pisanie, **_creat** obcina plik do długości 0, niszczy poprzednią zawartość i otwiera je do zapisu. Ustawienie uprawnienia *PMODE*ma zastosowanie tylko do nowo utworzonych plików. Nowy plik otrzymuje określone ustawienie uprawnienia po jego pierwszym zamknięciu. Wyrażenie Integer *PMODE* zawiera jedną lub obie stałe manifestu **_S_IWRITE** i **_S_IREAD**, zdefiniowane w SYS\Stat.h. Po otrzymaniu obu stałych są one przyłączone do operatora bitowego or ( **&#124;** ). Parametr *PMODE* jest ustawiony na jedną z następujących wartości.

|Wartość|Definicja|
|-----------|----------------|
|**_S_IWRITE**|Dozwolone jest zapisanie.|
|**_S_IREAD**|Odczytywanie dozwolone.|
|**_S_IREAD** &#124; **_S_IWRITE**|Dozwolone odczytywanie i zapisywanie.|

Jeśli nie podano uprawnienia do zapisu, plik jest tylko do odczytu. Wszystkie pliki są zawsze do odczytu; nie można przyznać uprawnień tylko do zapisu. Tryby **_S_IWRITE** i **_S_IREAD** | **_S_IWRITE** są równoważne. Pliki otwarte przy użyciu **_creat** są zawsze otwierane w trybie zgodności (zobacz [_sopen](sopen-wsopen.md)) z **_SH_DENYNO**.

**_creat** przed ustawieniem uprawnień (patrz [_umask](umask.md)) stosuje się do *PMODE* bieżącej maski uprawnień pliku. **_creat** jest zapewniana głównie w celu zapewnienia zgodności z poprzednimi bibliotekami. Wywołanie **_open** z **_O_CREAT** i **_O_TRUNC** w parametrze *Oflag* jest równoważne z **_creat** i jest preferowane dla nowego kodu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_creat**|\<IO. h>|\<sys/Types. h>, \<sys/stat. h>, \<errno. h>|
|**_wcreat**|\<IO. h> lub \<WCHAR. h>|\<sys/Types. h>, \<sys/stat. h>, \<errno. h>|

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

## <a name="see-also"></a>Zobacz też

[We/wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>
