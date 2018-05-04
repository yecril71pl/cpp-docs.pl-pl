---
title: fopen_s —, _wfopen_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wfopen_s
- fopen_s
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
- fopen_s
- _tfopen_s
- _wfopen_s
dev_langs:
- C++
helpviewer_keywords:
- _wfopen_s function
- opening files, for file I/O
- _tfopen_s function
- tfopen_s function
- wfopen_s function
- fopen_s function
- Unicode [C++], creating files
- Unicode [C++], writing files
- files [C++], opening
- Unicode [C++], files
ms.assetid: c534857e-39ee-4a3f-bd26-dfe551ac96c3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bef5587188cebe4ed7e91cbd95eb46cca7f05044
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="fopens-wfopens"></a>fopen_s, _wfopen_s

Otwiera plik. Te wersje programu [fopen —, _wfopen —](fopen-wfopen.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t fopen_s(
   FILE** pFile,
   const char *filename,
   const char *mode
);
errno_t _wfopen_s(
   FILE** pFile,
   const wchar_t *filename,
   const wchar_t *mode
);
```

### <a name="parameters"></a>Parametry

*pFile*<br/>
Wskaźnik do wskaźnika pliku, który zostanie wyświetlony wskaźnik do otwartego pliku.

*Nazwa pliku*<br/>
Nazwa pliku.

*Tryb*<br/>
Dozwolonego typu dostępu.

## <a name="return-value"></a>Wartość zwracana

Zero w przypadku powodzenia; błąd o kodzie błędu. Zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat kodów błędów.

### <a name="error-conditions"></a>Warunki błędów

|*pFile*|*Nazwa pliku*|*Tryb*|Wartość zwracana|Zawartość *pFile*|
|-------------|----------------|------------|------------------|------------------------|
|**NULL**|wszystkie|wszystkie|**EINVAL —**|Bez zmian|
|wszystkie|**NULL**|wszystkie|**EINVAL —**|Bez zmian|
|wszystkie|wszystkie|**NULL**|**EINVAL —**|Bez zmian|

## <a name="remarks"></a>Uwagi

Pliki, które są otwarte przez **fopen_s —** i **_wfopen_s —** nie są zabezpieczać. Jeśli potrzebujesz, że plik można zabezpieczać, użyj [_fsopen —, _wfsopen —](fsopen-wfsopen.md) z odpowiedniego udostępniania stałą tryb — na przykład **_sh_denyno —** udostępniania odczytu/zapisu.

**Fopen_s —** funkcja otwiera plik, który jest określony przez *filename*. **_wfopen_s —** jest wersja znaków dwubajtowych **fopen_s —**; argumenty **_wfopen_s —** są ciągami znaków dwubajtowych. **_wfopen_s —** i **fopen_s —** zachowują się tak samo w przeciwnym razie wartość.

**fopen_s —** akceptuje ścieżek, które są prawidłowe w systemie plików w punkcie wykonywania; Ścieżki UNC ani ścieżki, obejmujących zamapowane dyski sieciowe są akceptowane przez **fopen_s —** tak długo, jak system, który jest wykonywany kod ma dostęp do udziału lub mapowany dysk sieciowy w czasie wykonywania. Podczas konstruowania ścieżki **fopen_s —**, nie są przenoszone założeń dotyczących dostępności dysków, ścieżek lub udziały sieciowe w środowisku wykonywania. Możesz użyć ukośnikami (/) lub ukośników odwrotnych (\\) jako separatorów katalog w ścieżce.

Te funkcje walidację ich parametrów. Jeśli *pFile*, *filename*, lub *tryb* jest wskaźnika o wartości null, te funkcje wygeneruje wyjątek nieprawidłowy parametr, zgodnie z opisem w [sprawdzanie poprawności parametru ](../../c-runtime-library/parameter-validation.md).

Zawsze sprawdzić wartość zwrotną, aby zobaczyć, czy funkcja zakończyła się pomyślnie, przed wykonaniem jakichkolwiek dalszych działań na plik. Jeśli wystąpi błąd, zostanie zwrócony kod błędu i zmiennej globalnej **errno** jest ustawiona. Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="unicode-support"></a>Obsługa formatu Unicode

**fopen_s —** obsługuje strumienie pliku Unicode. Aby otworzyć nowy lub istniejący plik Unicode, należy przekazać *ccs* Flaga, która określa żądaną kodowanie **fopen_s —**:

**fopen_s — (& fp, "NowyPlik.txt", "rw, ccs =**_kodowanie_**");**

Dozwolone wartości *kodowanie* są **UNICODE**, **UTF-8**, i **UTF-16LE**. Jeśli istnieje nie określono wartości dla *kodowanie*, **fopen_s —** używa kodowania ANSI.

Jeśli plik już istnieje i jest otwarty do odczytu lub dołączania, Byte kolejności znaku (BOM), jeśli jest obecny w pliku Określa kodowanie. Kodowanie BOM pierwszeństwo nad kodowanie określonym przez *ccs* flagi. *Ccs* kodowanie jest używana tylko podczas BOM nie jest obecny lub jeśli plik jest nowy plik.

> [!NOTE]
> Wykrywanie BOM ma zastosowanie tylko do plików, które będą otwierane w trybie Unicode; oznacza to, że przekazywanie przez *ccs* flagi.

W poniższej tabeli przedstawiono metody dla różnych *ccs* flagi, które mają **fopen_s —** i znaczniki kolejności bajtów w pliku.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Na podstawie używane kodowanie ccs flagę i BOM

|Flaga ccs|Nie BOM (lub nowy plik)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Plików otwieranych w trybie Unicode mają BOM automatycznie zapisywane do nich.

Jeśli *tryb* jest **", ccs =**_kodowanie_**"**, **fopen_s —** po raz pierwszy próbuje otworzyć plik z odczytu dostęp i do zapisu. Jeśli to się powiedzie, funkcja odczytuje BOM, aby określić kodowanie pliku; w przypadku niepowodzenia funkcji używa domyślne kodowanie używane do pliku. W obu przypadkach **fopen_s —** ponowne otwarcie pliku z dostępem tylko do zapisu. (Dotyczy to **a** nie tylko w trybie **a+**.)

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen_s —**|**fopen_s —**|**fopen_s —**|**_wfopen_s**|

Ciąg znaków *tryb* określa rodzaj dostępu do żądanego pliku, w następujący sposób.

|*Tryb*|Access|
|-|-|
**"r"**|Zostanie otwarty do odczytu. Jeśli plik nie istnieje lub nie można znaleźć, **fopen_s —** wywołać kończy się niepowodzeniem.
**"w"**|Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaną zniszczone.
**""**|Zostanie otwarty do zapisu na końcu pliku (dołączanie) bez usuwania znacznika końca pliku (EOF), zanim nowe dane zostają zapisane do pliku. Tworzy plik, jeśli nie istnieje.
**"r +"**|Otwiera odczytywanie i zapisywanie. Plik musi istnieć.
**"w +"**|Otwiera pusty plik na odczytywanie i zapisywanie. Jeśli plik istnieje, jego zawartość zostaną zniszczone.
**"+"**|Zostanie otwarty do odczytu i dołączenie kodu. Dołączanie operacja obejmuje usunięcie znacznik EOF przed nowe dane zostają zapisane do pliku. Znacznik EOF nie jest przywracany po zakończeniu zapisu. Tworzy plik, jeśli nie istnieje.

Gdy plik jest otwarty przy użyciu **""** lub **"+"** dostęp typu, zapisać wszystkie operacje wykonywane na końcu pliku. Można można zmieniać ich położenia wskaźnika pliku przy użyciu [fseek](fseek-fseeki64.md) lub [rewind](rewind.md), ale on jest zawsze przeniesiony z powrotem na koniec pliku przed żadnego zapisu operacji odbywa się tak, aby nie można zastąpić istniejące dane.

**""** Trybu nie powoduje usunięcia znacznik EOF przed dołączeniem do pliku. Po wystąpił dołączanie polecenia typu MS-DOS przedstawia tylko danych do oryginalnej znacznik EOF, a nie dane, które są dołączane do pliku. **"+"** Tryb, usuń znacznik EOF przed dołączeniem do pliku. Po dołączeniu, polecenie typu MS-DOS Wyświetla wszystkie dane w pliku. **"+"** Tryb jest wymagany do dołączenia do strumienia pliku, który zostanie zakończony za pomocą znacznik EOF CTRL + Z.

Gdy **"r +"**, **"w +"**, lub **"+"** określono typ dostępu, odczytywanie i zapisywanie są dozwolone. (Plik jest określany jako otwarte dla "update"). Jednak po przełączeniu odczytu do zapisu operacji wejściowy musi wystąpić znacznik EOF. Jeśli nie ma żadnych EOF, należy użyć pośredniczące wywołania funkcji położenie pliku. Położenie pliku funkcje są **fsetpos —**, [fseek](fseek-fseeki64.md), i [rewind](rewind.md). Po przełączeniu zapisywania do odczytu, musisz użyć wywołania pośredniczące **fflush —** lub funkcji położenie pliku.

Oprócz powyższych wartości następujące znaki mogą być zawarte w *tryb* Aby określić tryb tłumaczenia na znaki nowego wiersza:

|*tryb* modyfikator|Tryb tłumaczenia|
|-|-|
**t**|Otwórz w tekście (translacji) trybu.
**b**|Otwórz w trybie binarnym (niezrozumiały); Tłumaczenie obejmujące znaki powrotu karetki i wysuwu wiersza są pomijane.

W trybie tekstowym (translacji) CTRL + Z jest interpretowany jako plik końcowy znak wejściowy. W plikach otwarty do odczytu/zapisu z **"+"**, **fopen_s —** wyszukuje klawisze CTRL + Z końcem pliku i usuwa go, jeśli to możliwe. Odbywa się, ponieważ używa [fseek](fseek-fseeki64.md) i **ftell —** można przenieść w pliku, który kończy się CTRL + Z, może spowodować [fseek](fseek-fseeki64.md) będzie działać nieprawidłowo zbliża się koniec pliku.

Ponadto w trybie tekstowym kombinacji wysuwu wiersza powrotu karetki są przekształcane na pojedynczy znaki wysuwu wiersza w danych wejściowych i wysuwu wiersza znaki są tłumaczone na kombinacje wysuwu wiersza powrotu karetki w danych wyjściowych. Jeśli funkcja strumienia I/O Unicode działa w trybie tekstowym (ustawienie domyślne), źródła lub strumień docelowy zakłada, że sekwencja znaków wielobajtowych. W związku z tym funkcji wejścia strumienia Unicode konwertuje znaki wielobajtowe na znaki dwubajtowe (tak jak w przypadku przez wywołanie do **mbtowc —** funkcji). Z tego samego powodu funkcje strumieni wyjściowych Unicode przekonwertować znaki dwubajtowe znaków wielobajtowych (tak jak w przypadku przez wywołanie do **wctomb —** funkcji).

Jeśli **t** lub **b** nie została podana w *tryb*, domyślny tryb tłumaczenia jest definiowana za pomocą zmiennej globalnej [_fmode —](../../c-runtime-library/fmode.md). Jeśli **t** lub **b** jest prefiksem argument, funkcja kończy się niepowodzeniem i zwraca **NULL**.

Aby uzyskać więcej informacji na temat używania trybach tekstowym i binarnym Unicode i wielobajtowe strumienia I/O zobacz [tekstu i we/wy binarne trybu pliku](../../c-runtime-library/text-and-binary-mode-file-i-o.md) i [we/wy strumienia w Unicode w trybach tekstowym i binarnym](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

|*tryb* modyfikator|Zachowanie|
|-|-|
**c**|Włącz flagę zatwierdzeń skojarzonych z nim *filename* tak, aby zawartość buforów plików są zapisywane bezpośrednio na dysku, jeśli dowolny **fflush —** lub **_flushall —** jest wywoływana.
**N**|Resetuj flagi zatwierdzeń skojarzonych z nim *filename* na "nie zatwierdzanie." Domyślnie włączone. Zastępuje ona również flagi globalne zatwierdzenia, gdy łącze programu z COMMODE.OBJ. Domyślnie flagi globalne zatwierdzania jest "nie-commit", chyba że zostaną jawnie połączone z programem z COMMODE. OBJ (zobacz [opcje łącza](../../c-runtime-library/link-options.md)).
**N**|Określa, że plik nie jest dziedziczona przez procesy podrzędne.
**S**|Określa, że buforowanie jest zoptymalizowana pod kątem, ale nie ograniczona do dostęp sekwencyjny z dysku.
**R**|Określa, że buforowanie jest zoptymalizowana pod kątem, ale nie ograniczona do dostępie swobodnym z dysku.
**T**|Określa plik jako tymczasowy. Jeśli to możliwe, nie jest opróżniany na dysku.
**D**|Określa plik jako tymczasowy. Jest ono usuwane po zamknięciu ostatniego wskaźnika pliku.
**ccs =**_kodowania_|Określa używany zestaw znaków zakodowanego (jeden z **UTF-8**, **UTF-16LE**, lub **UNICODE**) dla tego pliku. Pozostaw nieokreślony, jeśli chcesz kodowania ANSI.

Prawidłowe znaki *tryb* parametry używane w **fopen_s —** i [_fdopen —](fdopen-wfdopen.md) odpowiadają *oflag* argumenty użyte w [_ Otwórz](open-wopen.md) i [_sopen —](sopen-wsopen.md), wykonując następujące czynności.

|Znaki w *tryb* ciągu|Odpowiednik *oflag* wartość _otwórz/_sopen —|
|-------------------------------|----------------------------------------------------|
|**a**|**_O_wronly —** &#124; **_o_append —** (zazwyczaj **_o_wronly —** &#124; **_o_creat —** &#124;** _o_append — **)|
|**+**|**_O_rdwr —** &#124; **_o_append —** (zazwyczaj **_o_rdwr —** &#124; **_o_append —** &#124; **_o_creat —** )|
|**r**|**_O_RDONLY —**|
|**r +**|**_O_RDWR —**|
|**w**|**_O_wronly —** (zazwyczaj **_o_wronly —** &#124; **_o_creat —** &#124;** _o_trunc — **)|
|**w +**|**_O_rdwr —** (zazwyczaj **_o_rdwr —** &#124; **_o_creat —** &#124; **_o_trunc —**)|
|**b**|**_O_BINARY —**|
|**t**|**_O_TEXT —**|
|**c**|Brak|
|**N**|Brak|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**ccs = UNICODE**|**_O_WTEXT**|
|**ccs = UTF-8**|**_O_UTF8**|
|**ccs = UTF-16LE**|**_O_UTF16**|

Jeśli używasz **rb** tryb, nie będzie trzeba portu kodu i oczekiwany odczyt partii pliku i/lub nie zależy Ci na zachowaniu wydajność sieci, plików mapowanych na pamięć Win32 może być również opcję.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fopen_s —**|\<stdio.h>|
|**_wfopen_s**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

**c**, **n**, i **t** *tryb* opcje są rozszerzenia Microsoft do **fopen_s —** i [_fdopen —](fdopen-wfdopen.md) i nie powinna być używana których przenośność ANSI jest potrzebne.

## <a name="example"></a>Przykład

```C
// crt_fopen_s.c
// This program opens two files. It uses
// fclose to close the first file and
// _fcloseall to close all remaining files.

#include <stdio.h>

FILE *stream, *stream2;

int main( void )
{
   errno_t err;

   // Open for read (will fail if file "crt_fopen_s.c" does not exist)
   err  = fopen_s( &stream, "crt_fopen_s.c", "r" );
   if( err == 0 )
   {
      printf( "The file 'crt_fopen_s.c' was opened\n" );
   }
   else
   {
      printf( "The file 'crt_fopen_s.c' was not opened\n" );
   }

   // Open for write
   err = fopen_s( &stream2, "data2", "w+" );
   if( err == 0 )
   {
      printf( "The file 'data2' was opened\n" );
   }
   else
   {
      printf( "The file 'data2' was not opened\n" );
   }

   // Close stream if it is not NULL
   if( stream )
   {
      err = fclose( stream );
      if ( err == 0 )
      {
         printf( "The file 'crt_fopen_s.c' was closed\n" );
      }
      else
      {
         printf( "The file 'crt_fopen_s.c' was not closed\n" );
      }
   }

   // All other files are closed:
   int numclosed = _fcloseall( );
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );
}
```

```Output
The file 'crt_fopen_s.c' was opened
The file 'data2' was opened
Number of files closed by _fcloseall: 1
```

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
