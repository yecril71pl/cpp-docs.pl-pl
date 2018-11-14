---
title: _open, _wopen
ms.date: 11/04/2016
apiname:
- _open
- _wopen
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
ms.openlocfilehash: 7ef28d6cafa0b74b50ee2c50ec380b8bd3aed79f
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327294"
---
# <a name="open-wopen"></a>_open, _wopen

Otwiera plik. Te funkcje są przestarzałe, ponieważ bardziej bezpieczne wersje są dostępne; zobacz [_sopen_s —, _wsopen_s —](sopen-s-wsopen-s.md).

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
Rodzaj dozwolone operacje.

*pmode*<br/>
Tryb uprawnień.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca deskryptor pliku dla otwartego pliku. Zwracana wartość-1 wskazuje błąd; w takim przypadku **errno** jest ustawiony na jedną z następujących wartości.

|errno wartość|Warunek|
|-|-|
| **EACCES** | Podjęto próbę otwarcia pliku tylko do odczytu do zapisywania pliku trybie współdzielenia nie zezwala na określonej operacji lub podana ścieżka jest katalogiem. |
| **EEXIST** | **_O_CREAT** i **_O_EXCL** flag określonych, ale *filename* już istnieje. |
| **EINVAL** | Nieprawidłowy *oflag* lub *pmode* argumentu. |
| **EMFILE** | Dostępnych jest więcej deskryptorów plików nie (za dużo plików otwartych). |
| **ENOENT** | Plik lub nie można odnaleźć ścieżki. |

Aby uzyskać więcej informacji na temat tych i innych kodach powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Otwórz** funkcji spowoduje otwarcie pliku określonego przez *filename* i przygotowuje je do odczytu lub zapisu, określony przez *oflag*. **_wopen —** to wersja znaku dwubajtowego **_otwórz**; *filename* argument **_wopen —** jest ciągiem znaku dwubajtowego. **_wopen —** i **_otwórz** zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_topen —**|**_otwórz**|**_otwórz**|**_wopen —**|

*oflag* powstaje wyrażeniem liczby całkowitej z co najmniej jeden z następujących stałych manifestu lub kombinacji stałych, które są zdefiniowane w \<fcntl.h >.

|*oflag* stałej|Zachowanie|
|-|-|
| **_O_APPEND** | Przesuwa wskaźnik myszy plików na koniec pliku przed każdej operacji zapisu. |
| **_O_BINARY** | Otwiera plik w trybie binarnym (nieprzetłumaczonym). (Zobacz [fopen —](fopen-wfopen.md) opis trybie binarnym.) |
| **_O_CREAT** | Tworzy plik i otwiera go do zapisu. Nie obowiązuje, jeżeli plik określony przez *filename* istnieje. *Pmode* argument jest wymagany, gdy **_O_CREAT** jest określony. |
| **_O_CREAT** &AMP;#124; **_O_SHORT_LIVED** | Tworzy plik jako tymczasowy, a jeśli to możliwe nie opróżnia na dysku. *Pmode* argument jest wymagany, gdy **_O_CREAT** jest określony. |
| **_O_CREAT** &AMP;#124; **_O_TEMPORARY** | Tworzy plik jako tymczasowy; plik zostanie usunięty po zamknięciu ostatniego deskryptor pliku. *Pmode* argument jest wymagany, gdy **_O_CREAT** jest określony. |
| **_O_CREAT**&AMP;#124; ` _O_EXCL` | Zwraca wartość błędu, jeśli w pliku określonym przez *filename* istnieje. Ma zastosowanie tylko wtedy, gdy jest używane z **_O_CREAT**. |
| **_O_NOINHERIT** | Uniemożliwia tworzenie deskryptora udostępnionego pliku. |
| **_O_RANDOM** | Określa, że buforowanie jest zoptymalizowane pod kątem, ale nie ogranicza się do dostępu losowego do dysku. |
| **_O_RDONLY** | Otwiera plik do odczytu tylko. Nie można określić za pomocą **_O_RDWR** lub **_O_WRONLY**. |
| **_O_RDWR** | Otwiera plik na odczyt i zapis. Nie można określić za pomocą **_O_RDONLY** lub **_O_WRONLY**. |
| **_O_SEQUENTIAL** | Określa, że buforowanie jest zoptymalizowane pod kątem, ale nie ogranicza się do dostępu sekwencyjnego do dysku. |
| **_O_TEXT** | Otwiera plik w trybie tekstowym (tłumaczonym). (Aby uzyskać więcej informacji, zobacz [tekstowych i binarnych We/Wy trybu](../../c-runtime-library/text-and-binary-mode-file-i-o.md) i [fopen —](fopen-wfopen.md).) |
| **_O_TRUNC** | Otwiera plik i obcina go na wartość zero length; Plik musi mieć uprawnienia do zapisu. Nie można określić za pomocą **_O_RDONLY**. **_O_TRUNC** używane z **_O_CREAT** otwiera istniejący plik lub tworzy plik. **Uwaga:** **_O_TRUNC** flagi niszczy zawartość określonego pliku. |
| **_O_WRONLY** | Otwiera plik do zapisywania tylko. Nie można określić za pomocą **_O_RDONLY** lub **_O_RDWR**. |
| **_O_U16TEXT** | Otwiera plik w trybie Unicode UTF-16. |
| **_O_U8TEXT** | Otwiera plik w trybie Unicode UTF-8. |
| **_O_WTEXT** | Otwiera plik w trybie Unicode. |

Aby określić tryb dostępu do pliku, należy określić **_O_RDONLY**, **_O_RDWR**, lub **_O_WRONLY**. Nie ma domyślne wartości dla trybu dostępu.

Jeśli **_O_WTEXT** służy do otwierania pliku do odczytu, **_otwórz** odczytuje początku tego pliku i sprawdza, czy znacznik kolejności bajtów (BOM). Jeśli występuje znak BOM, plik jest traktowany jako UTF-8 lub UTF-16LE, w zależności od BOM. Jeśli znak BOM nie jest obecny, plik jest traktowany jako ANSI. Gdy plik jest otwarty do zapisu przy użyciu **_O_WTEXT**, UTF-16 jest używany. Niezależnie od tego, dowolnego poprzedniego ustawienia lub bajt znacznik kolejności, jeśli **_O_U8TEXT** jest używany, plik jest zawsze otwierany jako UTF-8; Jeśli **_O_U16TEXT** jest używany, plik jest zawsze otwierany jako UTF-16.

Po otwarciu pliku w trybie Unicode przy użyciu **_O_WTEXT**, **_O_U8TEXT**, lub **_O_U16TEXT**, wprowadź funkcji tłumaczenia danych, które są odczytywane z pliku danych UTF-16 przechowywane jako typ **wchar_t**. Funkcje, które zapisu do pliku, który został otwarty w trybie Unicode oczekiwać buforów, które zawierają dane UTF-16 przechowywane jako typ **wchar_t**. Jeśli plik jest zakodowany w formacie UTF-8, UTF-16 dane są tłumaczone na UTF-8 są zapisywane, gdy algorytmem UTF-8 zawartości jest tłumaczony na UTF-16, została przeczytana. Podjęto próbę odczytu lub zapisu nieparzystą liczbę bajtów w trybie Unicode powoduje błąd sprawdzania poprawności parametrów. Do odczytu lub zapisu danych przechowywanych w programach w formacie UTF-8, należy użyć trybu plików tekstowych lub binarnych zamiast trybie Unicode. Odpowiedzialność za wszelkie wymagane tłumaczenia kodowania.

Jeśli **_otwórz** jest wywoływana z **_O_WRONLY** | **_O_APPEND** (Dołącz tryb) i **_O_WTEXT**, **_O_ U16TEXT**, lub **_O_U8TEXT**, najpierw próbuje otworzyć plik do odczytu i zapisu, odczytu BOM, a następnie otwórz go ponownie do zapisywania tylko. Jeśli otwierania pliku do odczytu i zapisu kończy się niepowodzeniem, zostanie otwarty plik do zapisywania tylko i użyje wartości domyślnej dla ustawienia trybu Unicode.

Gdy dwa lub więcej stałych manifestu są używane do formularza *oflag* argument, stałe są łączone za pomocą operatora bitowego OR ( **&#124;** ). Omówienie binarnych i tekstowych trybów, zobacz [tekstowych i binarnych We/Wy trybu](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

*Pmode* argument jest wymagany tylko wtedy, gdy **_O_CREAT** jest określony. Jeśli plik już istnieje, *pmode* jest ignorowana. W przeciwnym razie *pmode* określa ustawienia uprawnień pliku, które są ustawione, gdy nowy plik jest zamknięty po raz pierwszy. **_otwórz** stosuje bieżące maskę uprawnień do pliku, aby *pmode* przed uprawnienia są ustawiane. (Aby uzyskać więcej informacji, zobacz [_umask —](umask.md).) *pmode* jest wyrażeniem liczby całkowitej, która zawiera jeden lub oba z następujących stałych manifestu, które są zdefiniowane w \<sys\stat.h >.

|*pmode*|Znaczenie|
|-|-|
| **_S_IREAD** | Dozwolone tylko odczyt. |
| **_S_IWRITE** | Zapisywanie jest dozwolone. (W praktyce pozwala na odczyt i zapis.) |
| **_S_IREAD** &AMP;#124; **_S_IWRITE** | Odczyt i zapis dozwolone. |

Gdy oba stałe są podane, są połączone za pomocą operatora bitowego OR ( **&#124;** ). W Windows wszystkie pliki są do odczytu; nie ma uprawnienia tylko do zapisu. W związku z tym, tryby **_S_IWRITE** i **_S_IREAD** | **_S_IWRITE** są równoważne.

Jeśli wartość inna niż kombinacji **_S_IREAD** i **_S_IWRITE** jest określona dla *pmode*— nawet jeśli należałoby określić prawidłową *pmode*w innym systemie operacyjnym — lub jeśli wszystkie wartości innych niż dozwolona *oflag* wartości jest określony, funkcja generuje potwierdzenie w trybie debugowania i wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca wartość -1 i ustawia **errno** do **EINVAL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_otwórz**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|
|**_wopen —**|\<IO.h > lub \<wchar.h >|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|

**_otwórz** i **_wopen —** są rozszerzeniami Microsoft. Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Zobacz także

[Niskiego poziomu operacji We/Wy](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
