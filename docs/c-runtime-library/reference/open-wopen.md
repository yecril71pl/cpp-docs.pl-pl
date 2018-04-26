---
title: _otwórz, _wopen — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 31
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b4b25e263d9483f308161a823b136643e1451106
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="open-wopen"></a>_open, _wopen

Otwiera plik. Te funkcje są przestarzałe, ponieważ bardziej bezpiecznych wersje są dostępne; zobacz [_sopen_s —, _wsopen_s —](sopen-s-wsopen-s.md).

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
Rodzaj operacji dozwolone.

*pmode*<br/>
Tryb uprawnień.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca deskryptor plik otwarty plik. Zwracana wartość -1 wskazuje błąd; w takim przypadku **errno** ustawiono na jedną z następujących wartości.

|errno wartość|Warunek|
|-|-|
**EACCES**|Podjęto próbę otwarcia pliku tylko do odczytu w celu zapisywania pliku trybie współdzielenia nie zezwala na określonej operacji lub podana ścieżka jest katalogiem.
**EEXIST —**|**_O_creat —** i **_o_excl —** flag określonych, ale *filename* już istnieje.
**EINVAL —**|Nieprawidłowy *oflag* lub *pmode* argumentu.
**EMFILE —**|Nie więcej deskryptorów plików są dostępne (zbyt wiele plików są otwarte).
**ENOENT —**|Plik lub nie można odnaleźć ścieżki.

Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Otwórz** funkcja otwiera plik określony przez *filename* i przygotowuje je do odczytu lub zapisu, określony przez *oflag*. **_wopen —** jest wersja znaków dwubajtowych **_otwórz**; *filename* argument **_wopen —** jest ciągiem znaków dwubajtowych. **_wopen —** i **_otwórz** zachowują się tak samo w przeciwnym razie wartość.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_topen —**|**_otwórz**|**_otwórz**|**_wopen —**|

*oflag* powstaje wyrażeniem liczby całkowitej z jedną lub więcej następujących stałych manifestu lub kombinacji stałej, które są zdefiniowane w \<fcntl.h >.

|*oflag* stałej|Zachowanie|
|-|-|
**_O_APPEND —**|Przenosi wskaźnika pliku koniec pliku przed każdej operacji zapisu.
**_O_BINARY —**|Otwiera plik w trybie binarnym (niezrozumiały). (Zobacz [fopen —](fopen-wfopen.md) opis trybie binarnym.)
**_O_CREAT —**|Tworzy plik i otwarcie go do zapisu. Nie ma efektu Jeśli plik określony przez *filename* istnieje. *Pmode* argumentu jest wymagany, gdy **_o_creat —** jest określona.
**_O_CREAT —** &AMP;#124; **_O_SHORT_LIVED**|Tworzy plik jako tymczasowy, a jeśli to możliwe nie mogło opróżnić na dysku. *Pmode* argumentu jest wymagany, gdy **_o_creat —** jest określona.
**_O_CREAT —** &AMP;#124; **_O_TEMPORARY**|Tworzy plik jako tymczasowy; plik zostanie usunięty po zamknięciu ostatniego deskryptorów plików. *Pmode* argumentu jest wymagany, gdy **_o_creat —** jest określona.
**_O_CREAT —**&AMP;#124; ` _O_EXCL`|Zwraca wartość błędu, jeśli plik określony przez *filename* istnieje. Ma zastosowanie tylko wtedy, gdy jest używany z **_o_creat —**.
**_O_NOINHERIT**|Uniemożliwia tworzenie deskryptora udostępnionych plików.
**_O_RANDOM**|Określa, że buforowanie jest zoptymalizowana pod kątem, ale nie ograniczona do dostępie swobodnym z dysku.
**_O_RDONLY —**|Otwiera plik tylko odczytywanie. Nie można określić za pomocą **_o_rdwr —** lub **_o_wronly —**.
**_O_RDWR —**|Otwiera plik na odczytywanie i zapisywanie. Nie można określić za pomocą **_o_rdonly —** lub **_o_wronly —**.
**_O_SEQUENTIAL**|Określa, że buforowanie jest zoptymalizowana pod kątem, ale nie ograniczona do dostęp sekwencyjny z dysku.
**_O_TEXT —**|Otwiera plik w trybie tekstowym (translacji). (Aby uzyskać więcej informacji, zobacz [tekstu i we/wy binarne trybu pliku](../../c-runtime-library/text-and-binary-mode-file-i-o.md) i [fopen —](fopen-wfopen.md).)
**_O_TRUNC —**|Otwiera plik i obcina go do zera length; Plik musi mieć uprawnienia do zapisu. Nie można określić za pomocą **_o_rdonly —**. **_O_trunc —** używane z **_o_creat —** otwiera istniejący plik lub tworzy plik. **Uwaga:** **_o_trunc —** flagi niszczy zawartość określonego pliku.
**_O_WRONLY —**|Otwiera plik do pisania tylko. Nie można określić za pomocą **_o_rdonly —** lub **_o_rdwr —**.
**_O_U16TEXT**|Otwiera plik w trybie Unicode UTF-16.
**_O_U8TEXT**|Otwiera plik w trybie Unicode UTF-8.
**_O_WTEXT**|Otwiera plik w trybie Unicode.

Aby określić tryb dostępu do pliku, należy określić **_o_rdonly —**, **_o_rdwr —**, lub **_o_wronly —**. Brak wartości domyślnej dla trybu dostępu.

Jeśli **_O_WTEXT** jest używany do otwierania pliku do odczytu, **_otwórz** odczytuje początku pliku i sprawdza, czy znacznik kolejności bajtów (BOM). W przypadku BOM, plik jest traktowane jako UTF-8 lub UTF-16LE, w zależności od BOM. Jeśli żaden BOM, plik jest traktowane jako ANSI. Gdy plik jest otwarty do zapisu przy użyciu **_O_WTEXT**, używane jest UTF-16. Niezależnie od tego, wszelkie poprzednie ustawienie lub byte znacznik kolejności, jeśli **_O_U8TEXT** jest używana, plik jest zawsze otwierany jako UTF-8; Jeśli **_O_U16TEXT** jest używana, jest zawsze otworzyć pliku jako UTF-16.

Gdy plik jest otwarty w trybie Unicode za pomocą **_O_WTEXT**, **_O_U8TEXT**, lub **_O_U16TEXT**, wejściowe funkcji tłumaczenie dane, które jest do odczytu z pliku na dane UTF-16 przechowywane jako typ **wchar_t**. Funkcje zapisu w pliku otwartym w trybie Unicode oczekiwać buforów, które zawierają dane UTF-16, przechowywane jako typ **wchar_t**. Jeśli plik jest zakodowany jako UTF-8, UTF-16 dane są tłumaczone na UTF-8 gdy jest ona zapisywana i pliku algorytmem UTF-8 zawartości jest przekształcana na UTF-16, została przeczytana. Próba odczytu lub zapisu nieparzystą liczbę bajtów w trybie Unicode powoduje błąd sprawdzania poprawności parametru. Do odczytu lub zapisu danych przechowywanych w programie jako UTF-8, tryb tekstowe lub binarne pliku zamiast trybu Unicode. Ponosisz odpowiedzialność za wszelkie wymagane tłumaczenia kodowania.

Jeśli **_otwórz** jest wywoływana z **_o_wronly —** | **_o_append —** (tryb dołączania) i **_O_WTEXT**, **_O_ U16TEXT**, lub **_O_U8TEXT**, po raz pierwszy próbuje otworzyć pliku do odczytu i zapisu, przeczytaj BOM, a następnie otwórz go ponownie w celu zapisywania tylko. Jeśli otwierania pliku do odczytu i zapisu kończy się niepowodzeniem, otwiera plik do zapisywania tylko i używa wartości domyślne ustawienie trybu Unicode.

Gdy dwa lub więcej manifestu stałe są używane do formularza *oflag* argumentu, stałe są łączone z operator Alternatywy ( **&#124;** ). Omówienie trybów pliku binarnego i tekstu, zobacz [tekstu i we/wy binarne trybu pliku](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

*Pmode* argumentu jest wymagany tylko wtedy, gdy **_o_creat —** jest określona. Jeśli plik już istnieje, *pmode* jest ignorowana. W przeciwnym razie *pmode* określa ustawienia uprawnień plików, które są ustawione, gdy nowy plik jest zamknięte po raz pierwszy. **_otwórz** stosuje bieżącą maskę pliku uprawnień do *pmode* przed uprawnienia zostały ustawione. (Aby uzyskać więcej informacji, zobacz [_umask —](umask.md).) *pmode* jest wyrażeniem liczby całkowitej, który zawiera co najmniej jednej z następujących stałych manifestu, które są zdefiniowane w \<sys\stat.h >.

|*pmode*|Znaczenie|
|-|-|
**_S_IREAD —**|Dozwolone tylko odczyt.
**_S_IWRITE —**|Zapisywanie dozwolone. (W praktyce umożliwia odczytywanie i zapisywanie.)
**_S_IREAD —** &AMP;#124; **_S_IWRITE —**|Odczytywanie i zapisywanie dozwolone.

Gdy zarówno stałe są podane, są połączone z operator Alternatywy ( **&#124;** ). W systemie Windows wszystkie pliki są do odczytu; nie ma uprawnienia tylko do zapisu. W związku z tym tryby **_s_iwrite —** i **_s_iread —** | **_s_iwrite —** są równoważne.

Jeśli wartość inną niż pewną kombinację wartości **_s_iread —** i **_s_iwrite —** określono *pmode*— nawet wtedy, gdy będzie Określ prawidłowe *pmode*w innym systemie operacyjnym, lub jeśli jakaś wartość inną niż dozwolona *oflag* określono wartości, funkcja generuje potwierdzenia w trybie debugowania i wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [Sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcja zwraca wartość -1 i zestawy **errno** do **einval —**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_otwórz**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|
|**_wopen —**|\<IO.h > lub \<wchar.h >|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|

**_otwórz** i **_wopen —** są rozszerzenia Microsoft. Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

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

[We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
