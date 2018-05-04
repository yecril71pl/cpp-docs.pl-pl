---
title: _creat —, _wcreat — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- wcreat function
- _wcreat function
- files [C++], creating
- _creat function
- tcreat function
- creat function
- _tcreat function
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 341ffb176a82845ec515e2ab2ff9a6d19b7773ea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
Ustawienie uprawnień.

## <a name="return-value"></a>Wartość zwracana

Te, w przypadku powodzenia zwracają deskryptorów plików do utworzonego pliku. W przeciwnym przypadku Zwróć -1, funkcje i ustaw **errno** zgodnie z poniższą tabelą.

|**errno** ustawienie|Opis|
|---------------------|-----------------|
|**EACCES**|*Nazwa pliku* Określa istniejący plik tylko do odczytu lub określa katalog, nie plikiem.|
|**EMFILE —**|Nie więcej deskryptorów plików są dostępne.|
|**ENOENT —**|Nie można odnaleźć określonego pliku.|

Jeśli *filename* ma wartość NULL, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji **errno** do **einval —** i zwróć -1.

Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Creat —** funkcji lub tworzy nowy plik otwiera i obcina już istniejący. **_wcreat —** jest wersja znaków dwubajtowych **_creat —**; *filename* argument **_wcreat —** jest ciągiem znaków dwubajtowych. **_wcreat —** i **_creat —** zachowują się tak samo w przeciwnym razie wartość.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat —**|**_creat**|**_creat**|**_wcreat**|

Jeśli plik określony przez *filename* nie istnieje, plik jest tworzony przy użyciu ustawienia dane uprawnienie i jest otwarty do zapisu. Jeśli plik już istnieje, a jego ustawienie uprawnień umożliwia zapisywanie, **_creat —** obcina plik ma długość 0, niszczenie zawartość poprzedniego i otwarcie go do zapisu. Ustawienie uprawnień *pmode*, dotyczy tylko nowo utworzone pliki. Nowy plik odbiera ustawienia określonego uprawnienia po jego zamknięciu po raz pierwszy. Wyrażenie całkowite *pmode* zawiera jeden lub oba manifestu stałe **_s_iwrite —** i **_s_iread —**zdefiniowanej w SYS\Stat.h. Gdy zarówno stałe są podane, są połączone z bitowego or — operator ( **&#124;** ). *Pmode* parametr jest ustawiony na jedną z następujących wartości.

|Wartość|Definicja|
|-----------|----------------|
|**_S_IWRITE —**|Zapisywanie dozwolone.|
|**_S_IREAD —**|Odczytywanie dozwolone.|
|**_S_IREAD —** &AMP;#124; **_S_IWRITE —**|Odczytywanie i zapisywanie dozwolone.|

Jeśli uprawnienia do zapisu nie zostanie podany, plik jest tylko do odczytu. Wszystkie pliki są zawsze do odczytu; Nie można udzielić uprawnienia tylko do zapisu. Tryby **_s_iwrite —** i **_s_iread —** | **_s_iwrite —** następnie są równoważne. Pliki otwierane przy użyciu **_creat —** są zawsze otwierane w trybie zgodności (zobacz [_sopen —](sopen-wsopen.md)) z **_sh_denyno —**.

**_creat —** stosuje bieżącą maskę pliku uprawnień do *pmode* przed ustawieniem uprawnienia (zobacz [_umask —](umask.md)). **_creat —** głównie w celu zachowania zgodności z poprzedniej biblioteki. Wywołanie **_otwórz** z **_o_creat —** i **_o_trunc —** w *oflag* parametru jest odpowiednikiem **_creat —**lub za nowy kod.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_creat**|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wcreat**|\<IO.h > lub \<wchar.h >|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

[We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>
