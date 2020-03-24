---
title: _open, _wopen
ms.date: 11/04/2016
api_name:
- _open
- _wopen
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
- _wopen
- _topen
- _open
helpviewer_keywords:
- opening files, for file I/O
- topen function
- _open function
- _topen function
- _wopen function
- files [C++], opening
- wopen function
- open function
ms.assetid: 13f6a0c3-d1aa-450d-a7aa-74abc91b163e
ms.openlocfilehash: 4ce6e9aebe5d058143ad737f9c9db5bb68b30b1f
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150732"
---
# <a name="_open-_wopen"></a>_open, _wopen

Otwiera plik. Te funkcje są przestarzałe, ponieważ dostępne są bardziej bezpieczne wersje; Zobacz [_sopen_s, _wsopen_s](sopen-s-wsopen-s.md).

## <a name="syntax"></a>Składnia

```C
int _open(
   const char *filename,
   int oflag [,
   int pmode]
);
int _wopen(
   const wchar_t *filename,
   int oflag [,
   int pmode]
);
```

### <a name="parameters"></a>Parametry

*Nazwa pliku*<br/>
Nazwa pliku.

*oflag*<br/>
Rodzaj operacji dozwolonych.

*pmode*<br/>
Tryb uprawnień.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca deskryptor pliku otwartego pliku. Zwracana wartość-1 wskazuje błąd; w takim przypadku **errno** jest ustawiony na jedną z następujących wartości.

|errno wartość|Warunek|
|-|-|
| **EACCES** | Podjęto próbę otwarcia pliku tylko do odczytu w celu zapisu, tryb udostępniania pliku nie zezwala na określone operacje lub podana ścieżka jest katalogiem. |
| **EEXIST** | Określono **_O_CREAT** i **_O_EXCL** flag, ale *filename* już istnieje. |
| **EINVAL** | Nieprawidłowy argument *Oflag* lub *PMODE* . |
| **EMFILE** | Nie ma więcej dostępnych deskryptorów plików (zbyt wiele otwartych plików). |
| **ENOENT** | Nie znaleziono pliku lub ścieżki. |

Aby uzyskać więcej informacji na temat tych i innych kodów powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_open** otwiera plik określony przez *filename* i przygotowuje go do odczytu lub zapisu, zgodnie z parametrem *Oflag*. **_wopen** to dwubajtowa wersja **_open**; argument *filename* **_wopen** jest ciągiem znaków dwubajtowych. **_wopen** i **_open** zachowują się identycznie w inny sposób.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_topen**|**_open**|**_open**|**_wopen**|

*Oflag* jest wyrażeniem liczby całkowitej, które zostało utworzone z co najmniej jednej z następujących stałych manifestu lub kombinacji stałych, które są zdefiniowane w \<fcntl. h >.

|stała *Oflag*|Zachowanie|
|-|-|
| **_O_APPEND** | Przenosi wskaźnik pliku na koniec pliku przed każdą operacją zapisu. |
| **_O_BINARY** | Otwiera plik w trybie binarnym (nieprzetłumaczonym). (Zobacz [fopen](fopen-wfopen.md) , aby zapoznać się z opisem trybu binarnego). |
| **_O_CREAT** | Tworzy plik i otwiera go do zapisu. Nie działa, jeśli istnieje plik określony przez *filename* . Argument *PMODE* jest wymagany, jeśli określono **_O_CREAT** . |
| **_O_CREAT** &#124; **_O_SHORT_LIVED** | Tworzy plik jako tymczasowy, a jeśli to możliwe, nie jest opróżniany na dysk. Argument *PMODE* jest wymagany, jeśli określono **_O_CREAT** . |
| **_O_CREAT** &#124; **_O_TEMPORARY** | Tworzy plik jako tymczasowy; plik zostanie usunięty po zamknięciu ostatniego deskryptora pliku. Argument *PMODE* jest wymagany, jeśli określono **_O_CREAT** . |
| **_O_CREAT** &#124; `_O_EXCL` | Zwraca wartość błędu, jeśli istnieje plik określony przez *nazwę* pliku. Ma zastosowanie tylko w przypadku, gdy jest używany z **_O_CREAT**. |
| **_O_NOINHERIT** | Uniemożliwia utworzenie deskryptora pliku udostępnionego. |
| **_O_RANDOM** | Określa, że buforowanie jest zoptymalizowane dla, ale nie ograniczone do, losowy dostęp z dysku. |
| **_O_RDONLY** | Otwiera plik tylko do odczytu. Nie można określić za pomocą **_O_RDWR** lub **_O_WRONLY**. |
| **_O_RDWR** | Otwiera plik do odczytu i zapisu. Nie można określić za pomocą **_O_RDONLY** lub **_O_WRONLY**. |
| **_O_SEQUENTIAL** | Określa, że buforowanie jest zoptymalizowane dla, ale nie ograniczone do, dostęp sekwencyjny z dysku. |
| **_O_TEXT** | Otwiera plik w trybie tekst (przetłumaczony). (Aby uzyskać więcej informacji, zobacz [plik tekstowy i tryb binarny we/wy](../../c-runtime-library/text-and-binary-mode-file-i-o.md) i [fopen](fopen-wfopen.md)). |
| **_O_TRUNC** | Otwiera plik i obcina jego długość do zera; plik musi mieć uprawnienia do zapisu. Nie można określić za pomocą **_O_RDONLY**. **_O_TRUNC** używany z **_O_CREAT** otwiera istniejący plik lub tworzy plik. **Uwaga:** Flaga **_O_TRUNC** niszczy zawartość określonego pliku. |
| **_O_WRONLY** | Otwiera plik tylko do zapisu. Nie można określić za pomocą **_O_RDONLY** lub **_O_RDWR**. |
| **_O_U16TEXT** | Otwiera plik w trybie Unicode UTF-16. |
| **_O_U8TEXT** | Otwiera plik w trybie Unicode UTF-8. |
| **_O_WTEXT** | Otwiera plik w trybie Unicode. |

Aby określić tryb dostępu do pliku, należy określić **_O_RDONLY**, **_O_RDWR**lub **_O_WRONLY**. Brak wartości domyślnej dla trybu dostępu.

Jeśli **_O_WTEXT** jest używany do otwierania pliku do odczytu, **_open** odczytuje początek pliku i wyszukuje znacznik kolejności bajtów (BOM). Jeśli istnieje BOM, plik jest traktowany jako UTF-8 lub UTF-16LE, w zależności od BOM. Jeśli BOM nie jest obecny, plik jest traktowany jako ANSI. Gdy plik jest otwierany do zapisu za pomocą **_O_WTEXT**, jest używany UTF-16. Niezależnie od poprzedniego ustawienia lub znacznika kolejności bajtów, jeśli użyto **_O_U8TEXT** , plik jest zawsze OTWIERANY jako UTF-8; Jeśli **_O_U16TEXT** jest używany, plik jest zawsze OTWIERANY jako UTF-16.

Gdy plik jest otwierany w trybie Unicode przy użyciu **_O_WTEXT**, **_O_U8TEXT**lub **_O_U16TEXT**, funkcje wejściowe przekładają dane odczytane z pliku do danych UTF-16 przechowywanych jako **wchar_t**typu. Funkcje, które zapisują do pliku otwartego w trybie Unicode, oczekują buforów zawierających dane w formacie UTF-16 przechowywane jako typ **wchar_t**. Jeśli plik jest zakodowany jako UTF-8, dane UTF-16 są tłumaczone na UTF-8 podczas zapisywania, a zawartość zakodowana w formacie UTF-8 jest tłumaczona na UTF-16 podczas odczytywania. Próba odczytania lub zapisania nieparzystej liczby bajtów w trybie Unicode powoduje błąd walidacji parametru. Aby odczytać lub zapisać dane, które są przechowywane w programie jako UTF-8, użyj trybu plików tekstowych lub binarnych zamiast trybu Unicode. Użytkownik jest odpowiedzialny za wszelkie wymagane tłumaczenia kodowania.

Jeśli **_open** jest wywoływana z **_O_WRONLY** |  **_O_APPEND** (tryb Append) i **_O_WTEXT**, **_O_U16TEXT**lub **_O_U8TEXT**, najpierw próbuje otworzyć plik do odczytu i zapisu, odczytać BOM, a następnie otworzyć go tylko do zapisu. Jeśli otwarcie pliku do odczytu i zapisu nie powiedzie się, otwiera plik wyłącznie do zapisu i używa wartości domyślnej dla ustawienia trybu Unicode.

Gdy co najmniej dwie stałe manifestu są używane do tworzenia argumentu *Oflag* , stałe są łączone z operatorem bitowym or ( **&#124;** ). Aby zapoznać się z omówieniem trybów binarnych i tekstowych, zobacz [plik tekstowy i tryb binarny we/wy](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Argument *PMODE* jest wymagany tylko wtedy, gdy określono **_O_CREAT** . Jeśli plik już istnieje, *PMODE* jest ignorowany. W przeciwnym razie *PMODE* określa ustawienia uprawnień plików, które są ustawiane, gdy nowy plik jest zamykany po raz pierwszy. **_open** stosuje bieżącą maskę uprawnień pliku do *PMODE* przed ustawieniem uprawnień. (Aby uzyskać więcej informacji, zobacz [_umask](umask.md).) *PMODE* jest wyrażeniem liczb całkowitych, które zawiera jedną lub obie poniższe stałe manifestu, które są zdefiniowane w \<sys\stat.h >.

|*pmode*|Znaczenie|
|-|-|
| **_S_IREAD** | Dozwolony jest tylko odczyt. |
| **_S_IWRITE** | Dozwolone jest zapisanie. (W efekcie zezwala na odczyt i zapis). |
| **_S_IREAD** &#124; **_S_IWRITE** | Dozwolone odczytywanie i zapisywanie. |

Po otrzymaniu obu stałych są one przyłączone do operatora bitowego lub ( **&#124;** ). W systemie Windows można odczytać wszystkie pliki; uprawnienie tylko do zapisu jest niedostępne. W związku z tym tryby **_S_IWRITE** i **_S_IREAD** |  **_S_IWRITE** są równoważne.

Jeśli określono wartość inną niż część **_S_IREAD** i **_S_IWRITE** dla *PMODE*— nawet jeśli określisz prawidłowy *PMODE* w innym systemie operacyjnym, lub jeśli jakakolwiek wartość inna niż dozwolone wartości *Oflag* jest określona, funkcja generuje potwierdzenie w trybie debugowania i wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca wartość-1 i ustawia **errno** na **EINVAL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_open**|\<we/wy >|\<fcntl. h >, \<sys\types.h >, \<sys\stat.h >|
|**_wopen**|\<we/wy > lub \<WCHAR. h >|\<fcntl. h >, \<sys\types.h >, \<sys\stat.h >|

**_open** i **_wopen** są rozszerzeniami firmy Microsoft. Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_open.c
// compile with: /W3
/* This program uses _open to open a file
* named CRT_OPEN.C for input and a file named CRT_OPEN.OUT
* for output. The files are then closed.
*/
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int fh1, fh2;

   fh1 = _open( "CRT_OPEN.C", _O_RDONLY ); // C4996
   // Note: _open is deprecated; consider using _sopen_s instead
   if( fh1 == -1 )
      perror( "Open failed on input file" );
   else
   {
      printf( "Open succeeded on input file\n" );
      _close( fh1 );
   }

   fh2 = _open( "CRT_OPEN.OUT", _O_WRONLY | _O_CREAT, _S_IREAD |
                            _S_IWRITE ); // C4996
   if( fh2 == -1 )
      perror( "Open failed on output file" );
   else
   {
      printf( "Open succeeded on output file\n" );
      _close( fh2 );
   }
}
```

### <a name="output"></a>Dane wyjściowe

```Output
Open succeeded on input file
Open succeeded on output file
```

## <a name="see-also"></a>Zobacz też

[We/wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
