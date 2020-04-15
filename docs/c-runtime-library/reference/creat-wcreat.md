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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 18ecf78d2cbff3647eae912a1bb1b17d5340f185
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348338"
---
# <a name="_creat-_wcreat"></a>_creat, _wcreat

Tworzy nowy plik. **_creat** i **_wcreat** zostały przestarzałe; _sopen_s, [zamiast tego _wsopen_s.](sopen-s-wsopen-s.md)

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

*Pod nazwą*<br/>
Nazwa nowego pliku.

*pmode*<br/>
Ustawienie uprawnień.

## <a name="return-value"></a>Wartość zwracana

Te funkcje, jeśli zakończy się pomyślnie, zwracają deskryptora pliku do utworzonego pliku. W przeciwnym razie funkcje zwracają -1 i ustawić **errno,** jak pokazano w poniższej tabeli.

|ustawienie **errno**|Opis|
|---------------------|-----------------|
|**EACCES ( EACCES )**|*nazwa pliku* określa istniejący plik tylko do odczytu lub określa katalog zamiast pliku.|
|**EMFILE (EMFILE)**|Nie ma już dostępnych deskryptorów plików.|
|**Enoent**|Nie można odnaleźć określonego pliku.|

Jeśli *nazwa pliku* ma wartość **NULL**, te funkcje wywołują nieprawidłowy program obsługi parametrów, zgodnie z opisem w polu Sprawdzanie [poprawności parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, te funkcje ustawić **errno** na **EINVAL** i zwracać -1.

Aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_creat** tworzy nowy plik lub otwiera i obcina istniejący plik. **_wcreat** jest szerokoznakową wersją **_creat**; *argumentnazyt,* który **ma _wcreat** jest ciągiem znaków o szerokim charakterze. **_wcreat** i **_creat** zachowują się identycznie w przeciwnym razie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

Jeśli plik określony przez *nazwę pliku* nie istnieje, nowy plik jest tworzony przy określonym ustawieniu uprawnień i jest otwierany do zapisu. Jeśli plik już istnieje, a jego ustawienie uprawnień umożliwia zapisywanie, **_creat** obcina plik do długości 0, niszcząc poprzednią zawartość i otwiera go do zapisu. Ustawienie uprawnień, *pmode,* dotyczy tylko nowo utworzonych plików. Nowy plik otrzymuje określone ustawienie uprawnień po jego zamknięciu po raz pierwszy. *Pmode* wyrażenia liczby całkowitej zawiera jedną lub obie stałe manifestu **_S_IWRITE** i **_S_IREAD**, zdefiniowane w SYS\Stat.h. Po podaniu obu stałych są one połączone z operatorem bitowy lub **(&#124;).** Parametr *pmode* jest ustawiony na jedną z następujących wartości.

|Wartość|Definicja|
|-----------|----------------|
|**_S_IWRITE**|Pisanie dozwolone.|
|**_S_IREAD**|Odczyt dozwolony.|
|**_S_IREAD _S_IWRITE** &#124; **&#124;**|Czytanie i pisanie dozwolone.|

Jeśli uprawnienie do zapisu nie jest podane, plik jest tylko do odczytu. Wszystkie pliki są zawsze czytelne; nie można udzielić uprawnień tylko do zapisu. Tryby **_S_IWRITE** i **_S_IREAD** | **_S_IWRITE** są wtedy równoważne. Pliki otwierane za pomocą **_creat** są zawsze otwierane w trybie zgodności (patrz [_sopen)](sopen-wsopen.md)z **_SH_DENYNO**.

**_creat** przed ustawieniem uprawnień zastosuje bieżącą maskę uprawnień do pliku do *pmode* (patrz [_umask](umask.md)). **_creat** jest dostępna przede wszystkim w celu zapewnienia zgodności z poprzednimi bibliotekami. Wywołanie **_open** z **_O_CREAT** i **_O_TRUNC** w *oflag* parametr jest odpowiednikiem **_creat** i jest korzystne dla nowego kodu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_creat**|\<> io.h|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wcreat**|\<io.h> lub \<wchar.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

[We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>
