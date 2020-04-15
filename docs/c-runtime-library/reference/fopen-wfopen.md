---
title: fopen, _wfopen
ms.date: 4/2/2020
api_name:
- _wfopen
- fopen
- _o__wfopen
- _o_fopen
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
- fopen
- _wfopen
- _tfopen
- corecrt_wstdio/_wfopen
- stdio/fopen
helpviewer_keywords:
- opening files, for file I/O
- wfopen function
- tfopen function
- _tfopen function
- _wfopen function
- files [C++], opening
- fopen function
ms.assetid: e868993f-738c-4920-b5e4-d8f2f41f933d
ms.openlocfilehash: 4b9fa6542996b2c16128a841e2611b85e995be2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346406"
---
# <a name="fopen-_wfopen"></a>fopen, _wfopen

Otwiera plik. Dostępne są bezpieczniejsze wersje tych funkcji, które wykonują dodatkowe sprawdzanie poprawności parametrów i kody błędów zwracanych; patrz [fopen_s, _wfopen_s](fopen-s-wfopen-s.md).

## <a name="syntax"></a>Składnia

```C
FILE *fopen(
   const char *filename,
   const char *mode
);
FILE *_wfopen(
   const wchar_t *filename,
   const wchar_t *mode
);
```

### <a name="parameters"></a>Parametry

*Pod nazwą*<br/>
Nazwa pliku.

*Tryb*<br/>
Rodzaj dostępu, który jest włączony.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do otwartego pliku. Wartość wskaźnika zerowego wskazuje błąd. Jeśli *nazwa pliku* lub *tryb* ma **wartość NULL** lub pusty ciąg, te funkcje wyzwalają nieprawidłowy program obsługi parametrów, który jest opisany w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, te funkcje zwracają **wartość NULL** i **ustawiają errno** na **EINVAL**.

Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **fopen** otwiera plik określony przez *nazwę pliku*. Domyślnie wąski ciąg *nazwy pliku* jest interpretowany przy użyciu strony kodowej ANSI (CP_ACP). W aplikacjach pulpitu systemu Windows można to zmienić na stronę kodową OEM (CP_OEMCP) za pomocą funkcji [SetFileApisToOEM.](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) Za pomocą funkcji [AreFileApisANSI](/windows/win32/api/fileapi/nf-fileapi-arefileapisansi) można określić, czy *nazwa pliku* jest interpretowana przy użyciu ansi lub domyślnej strony kodowej OEM systemu. **_wfopen** jest szerokoznakową wersją **fopena;** argumenty, które **mają _wfopen,** to ciągi znaków o szerokich znakach. W przeciwnym razie **_wfopen** i **fopen** zachowują się identycznie. Samo użycie **_wfopen** nie ma wpływu na zakodowany zestaw znaków, który jest używany w strumieniu plików.

**fopen** akceptuje ścieżki, które są prawidłowe w systemie plików w punkcie wykonania; **fopen** akceptuje ścieżki UNC i ścieżki, które obejmują mapowane dyski sieciowe, tak długo, jak system, który wykonuje kod ma dostęp do udziału lub mapowany dysk w momencie wykonywania. Podczas konstruowania ścieżek dla **fopen,** upewnij się, że dyski, ścieżki lub udziały sieciowe będą dostępne w środowisku wykonywania. Jako separatory katalogów w ścieżce można użyć\\ukośników (/) lub ukośników odwrotnych ( ) (

Zawsze sprawdź wartość zwracaną, aby zobaczyć, czy wskaźnik ma wartość NULL przed wykonaniem dodatkowych operacji w pliku. Jeśli wystąpi błąd, zmienna globalna **errno** jest ustawiona i może służyć do uzyskania określonych informacji o błędzie. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="unicode-support"></a>Obsługa formatu Unicode

**fopen** obsługuje strumienie plików Unicode. Aby otworzyć plik Unicode, przekaż flagę **ccs** określającą żądane kodowanie do **fopenu**w następujący sposób.

> **FILE \*fp = fopen("newfile.txt", "rt+, ccs=**_kodowanie_**");**

Dozwolone wartości *kodowania* to **UNICODE**, **UTF-8**i **UTF-16LE**.

Gdy plik jest otwierany w trybie Unicode, funkcje wejściowe tłumaczą dane odczytywane z pliku na dane UTF-16 przechowywane jako typ **wchar_t**. Funkcje zapisu, które zapisują do pliku otwartego w trybie Unicode, oczekują buforów zawierających dane UTF-16 przechowywane jako **typ wchar_t**. Jeśli plik jest zakodowany jako UTF-8, następnie UTF-16 dane są tłumaczone na UTF-8, gdy jest zapisywany, a plik UTF-8 zakodowane zawartość jest tłumaczona na UTF-16, gdy jest odczytywany. Próba odczytu lub zapisu nieparzystej liczby bajtów w trybie Unicode powoduje błąd [sprawdzania poprawności parametru.](../../c-runtime-library/parameter-validation.md) Aby odczytać lub zapisać dane przechowywane w programie jako UTF-8, użyj trybu tekstowego lub binarnego zamiast trybu Unicode. Użytkownik jest odpowiedzialny za wszelkie wymagane tłumaczenie kodowania.

Jeśli plik już istnieje i jest otwarty do odczytu lub dołączania, znak bom (Byte Order Mark), jeśli znajduje się w pliku, określa kodowanie. Kodowanie BOM ma pierwszeństwo przed kodowaniem określonym przez flagę **ccs.** Kodowanie **ccs** jest używane tylko wtedy, gdy nie ma BOM lub plik jest nowy plik.

> [!NOTE]
> Wykrywanie BOM dotyczy tylko plików, które są otwierane w trybie Unicode (czyli przez przekazanie flagi **ccs).**

W poniższej tabeli podsumowano tryby używane dla różnych flag **ccs** nadanych **znakom fopen** i Byte Order Marks w pliku.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Kodowanie używane na podstawie flagi ccs i BOM

|flaga ccs|Brak BOM (lub nowego pliku)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**Unicode**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Pliki otwarte do zapisu w trybie Unicode mają BOM zapisywane do nich automatycznie.

Jeśli *tryb* jest **"a, ccs =**_kodowanie_**",** **fopen** najpierw próbuje otworzyć plik przy użyciu dostępu do odczytu i zapisu. Jeśli to się powiedzie, funkcja odczytuje BOM w celu określenia kodowania pliku; Jeśli to się nie powiedzie, funkcja używa domyślnego kodowania pliku. W obu przypadkach **fopen** ponownie otworzy plik przy użyciu dostępu tylko do zapisu. (Dotyczy to tylko trybu **"a",** a nie trybu **"a+").)**

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**Fopen**|**Fopen**|**_wfopen**|

*Tryb* ciągu znaków określa rodzaj dostępu, który jest wymagany dla pliku, w następujący sposób.

|*Tryb*|Dostęp|
|-|-|
| **"r"** | Otwiera się do czytania. Jeśli plik nie istnieje lub nie można go odnaleźć, **wywołanie fopen** nie powiedzie się. |
| **"w"** | Otwiera pusty plik do zapisania. Jeśli dany plik istnieje, jego zawartość zostanie zniszczona. |
| **"a"** | Otwiera się do zapisu na końcu pliku (dołączanie) bez usuwania znacznika końca pliku (EOF) przed zapisaniem nowych danych w pliku. Tworzy plik, jeśli nie istnieje. |
| **"r+"** | Otwiera się zarówno do czytania, jak i pisania. Plik musi istnieć. |
| **"w+"** | Otwiera pusty plik do odczytu i zapisu. Jeśli plik istnieje, jego zawartość zostanie zniszczona. |
| **"a+"** | Otwiera do czytania i dołączania. Operacja dołączania obejmuje usunięcie znacznika EOF przed zapisaniem nowych danych w pliku. Znacznik EOF nie zostanie przywrócony po zakończeniu zapisu. Tworzy plik, jeśli nie istnieje. |

Gdy plik jest otwierany przy użyciu typu dostępu **"a"** lub typu dostępu **"a+",** wszystkie operacje zapisu występują na końcu pliku. Wskaźnik pliku można zmienić położenie za pomocą [fseek](fseek-fseeki64.md) lub [przewijania](rewind.md)do tyłu , ale jest zawsze przenoszony z powrotem na koniec pliku przed wykonaniem jakiejkolwiek operacji zapisu. W związku z tym istniejące dane nie mogą być zastąpione.

Tryb **"a"** nie usuwa znacznika EOF przed dołączeniem go do pliku. Po dołączeniu polecenie MS-DOS TYPE pokazuje tylko dane do oryginalnego znacznika EOF, a nie wszystkie dane dołączone do pliku. Zanim zostanie dołączona do pliku, tryb **"a+"** usuwa znacznik EOF. Po dołączeniu polecenie MS-DOS TYPE pokazuje wszystkie dane w pliku. Tryb **"a+"** jest wymagany do dołączania do pliku strumienia, który jest zakończony znacznikiem CTRL+Z EOF.

Po określeniu typu dostępu **"r+",** **"w+"** lub **"a+"** włączone są zarówno odczytywanie, jak i zapisywanie (mówi się, że plik jest otwarty dla "aktualizacji"). Jednak po przełączeniu z odczytu do zapisu, operacja wprowadzania musi napotkać znacznik EOF. Jeśli nie ma eof, należy użyć interweniującego wywołania funkcji pozycjonowania plików. Funkcje pozycjonowania plików to **fsetpos**, [fseek](fseek-fseeki64.md)i [przewijanie do tyłu.](rewind.md) Po przełączeniu się z zapisu do odczytu, należy użyć interweniującego wywołania albo **fflush** lub funkcji pozycjonowania pliku.

Oprócz wcześniejszych wartości do *trybu* można dołączyć następujące znaki, aby określić tryb tłumaczenia dla znaków nowego.

|modyfikator *trybu*|Tryb tłumaczenia|
|-|-|
| **t** | Otwórz w trybie tekstowym (przetłumaczonym). |
| **B** | Otwarte w trybie binarnym (nieprzetłumaczonym); tłumaczenia obejmujące znaki powrotu karetki i wiersza są pomijane. |

W trybie tekstowym ctrl+Z jest interpretowany jako znak EOF na danych wejściowych. W plikach, które są otwierane do odczytu/zapisu za pomocą **"a+",** **fopen** sprawdza, czy ctrl+ Z na końcu pliku i usuwa go, jeśli jest to możliwe. Dzieje się tak, ponieważ za pomocą [fseek](fseek-fseeki64.md) i **ftell** przenieść w pliku, który kończy się CTRL + Z może spowodować [fseek](fseek-fseeki64.md) zachowywać się nieprawidłowo na końcu pliku.

W trybie tekstowym kombinacje podawania wiersza powrotu karetki są tłumaczone na pojedyncze kanały informacyjne na danych wejściowych, a znaki posuwu wiersza są tłumaczone na kombinacje posuwu wiersza powrotu karetki na wyjściu. Gdy funkcja strumienia Unicode we/wy działa w trybie tekstowym (domyślnie), przyjmuje się, że strumień źródłowy lub docelowy jest sekwencją znaków wielobajtowych. W związku z tym funkcje wejścia strumieniowego Unicode konwertują znaki wielobajtowe na znaki szerokie (tak jakby przez wywołanie funkcji **mbtowc).** Z tego samego powodu funkcje wyjścia strumieniowego Unicode konwertują znaki szerokokątne na znaki wielobajtowe (tak jakby przez wywołanie funkcji **wctomb).**

Jeśli **t** lub **b** nie jest podany w *trybie,* domyślny tryb tłumaczenia jest zdefiniowany przez zmienną globalną [_fmode](../../c-runtime-library/fmode.md). Jeśli **argument jest** poprzedzony t lub **b,** funkcja kończy się niepowodzeniem i zwraca **wartość NULL**.

Aby uzyskać więcej informacji na temat używania tekstu i trybów binarnych w trybie Unicode i wielobajtowym strumieniu We/Wy, zobacz [We/Wy pliku tekstowego i binarnego oraz](../../c-runtime-library/text-and-binary-mode-file-i-o.md) [We/Wy strumienia Unicode w trybach tekstowych i binarnych](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Następujące opcje można dołączyć do *trybu,* aby określić dodatkowe zachowania.

|modyfikator *trybu*|Zachowanie|
|-|-|
| **C** | Włącz flagę zatwierdzania skojarzonej *nazwy pliku,* tak aby zawartość buforu plików była zapisywana bezpośrednio na dysku, jeśli wywoływana jest **nazwa fflush** lub **_flushall.** |
| **N** | Zresetuj flagę zatwierdzania skojarzonej *nazwy pliku* na "no-commit". Domyślnie włączone. Zastępuje również globalną flagę zatwierdzania, jeśli program zostanie powiązany z plikiem COMMODE.OBJ. Domyślna flaga zatwierdzania globalnego to "no-commit", chyba że program zostanie jawnie powiązany z programem COMMODE. OBJ (patrz [Opcje łącza).](../../c-runtime-library/link-options.md) |
| **N** | Określa, że plik nie jest dziedziczony przez procesy podrzędne. |
| **S** | Określa, że buforowanie jest zoptymalizowane pod kątem sekwencyjnego dostępu z dysku, ale nie ogranicza się do niego. |
| **R** | Określa, że buforowanie jest zoptymalizowane pod kątem losowego dostępu z dysku, ale nie ogranicza się do niego. |
| **T** | Określa plik jako tymczasowy. Jeśli to możliwe, nie jest opróżniany na dysk. |
| **D** | Określa plik jako tymczasowy. Jest on usuwany po zamknięciu ostatniego wskaźnika pliku. |
| **ccs =**_kodowanie_ | Określa zakodowany zestaw znaków do użycia (jeden z **UTF-8**, **UTF-16LE**lub **UNICODE**) dla tego pliku. Pozostaw nieokreślony, jeśli chcesz kodować ANSI. |

Prawidłowe znaki dla ciągu *trybu* używanego w **fopen** i **_fdopen** odpowiadają argumentom *oflag,* które są używane w [_open](open-wopen.md) i [_sopen,](sopen-wsopen.md)w następujący sposób.

|Znaki w *ciągu trybu*|Równoważna *wartośćlagowa* \_\_dla open/ sopen|
|-------------------------------|----------------------------------------------------|
|**A**|**\_O\_WRONLY** &#124; ** \_O\_APPEND** (zwykle ** \_O\_WRONLY** &#124; ** \_\_O CREAT** &#124; ** \_O\_APPEND)**|
|**a+**|**\_O\_RDWR** &#124; ** \_O\_APPEND** (zwykle ** \_O\_RDWR** &#124; ** \_O\_APPEND** &#124; ** \_O\_CREAT)**|
|**R**|**\_O\_RDONLY**|
|**r+**|**\_O\_RDWR**|
|**W**|**\_O\_WRONLY** (zwykle ** \_\_O WRONLY** &#124; ** \_\_O CREAT** &#124; ** \_O\_TRUNC)**|
|**w+**|**\_O\_RDWR** (zwykle ** \_\_O RDWR** &#124; ** \_\_O CREAT** &#124; ** \_O\_TRUNC)**|
|**B**|**\_O\_BINARNY**|
|**t**|**\_O\_TEKST**|
|**C**|Brak|
|**N**|Brak|
|**S**|**\_O\_SEKWENCYJNE**|
|**R**|**\_O\_LOSOWO**|
|**T**|**\_O\_KRÓTKOTRWAŁE**|
|**D**|**\_O\_TYMCZASOWE**|
|**ccs=UNICODE**|**\_O\_WTEXT**|
|**ccs=UTF-8**|**\_z\_o. UTF8**|
|**ccs=UTF-16LE**|**\_z\_o. UTF16**|

Jeśli używasz trybu **rb,** nie musisz przenosić kodu, a jeśli spodziewasz się przeczytać większość dużego pliku lub nie martwisz się o wydajność sieci, możesz również rozważyć, czy użyć pamięci mapowanych plików Win32 jako opcji.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**Fopen**|\<stdio.h>|
|**_wfopen**|\<stdio.h> lub \<wchar.h>|

**_wfopen** jest rozszerzeniem firmy Microsoft. Aby uzyskać więcej informacji na temat zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

Opcje *trybu* **c**, **n**, **t**, **S,** **R,** **T**i **D** są rozszerzeniami firmy Microsoft dla **fopen** i **_fdopen** i nie powinny być używane tam, gdzie wymagana jest przenośność ANSI.

## <a name="example-1"></a>Przykład 1

Poniższy program otwiera dwa pliki.  Używa **fclose,** aby zamknąć pierwszy plik i **_fcloseall,** aby zamknąć wszystkie pozostałe pliki.

```C
// crt_fopen.c
// compile with: /W3
// This program opens two files. It uses
// fclose to close the first file and
// _fcloseall to close all remaining files.

#include <stdio.h>

FILE *stream, *stream2;

int main( void )
{
   int numclosed;

   // Open for read (will fail if file "crt_fopen.c" does not exist)
   if( (stream  = fopen( "crt_fopen.c", "r" )) == NULL ) // C4996
   // Note: fopen is deprecated; consider using fopen_s instead
      printf( "The file 'crt_fopen.c' was not opened\n" );
   else
      printf( "The file 'crt_fopen.c' was opened\n" );

   // Open for write
   if( (stream2 = fopen( "data2", "w+" )) == NULL ) // C4996
      printf( "The file 'data2' was not opened\n" );
   else
      printf( "The file 'data2' was opened\n" );

   // Close stream if it is not NULL
   if( stream)
   {
      if ( fclose( stream ) )
      {
         printf( "The file 'crt_fopen.c' was not closed\n" );
      }
   }

   // All other files are closed:
   numclosed = _fcloseall( );
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );
}
```

```Output
The file 'crt_fopen.c' was opened
The file 'data2' was opened
Number of files closed by _fcloseall: 1
```

## <a name="example-2"></a>Przykład 2

Poniższy program tworzy plik (lub zastępuje jeden, jeśli istnieje), w trybie tekstowym, który ma kodowanie Unicode.  Następnie zapisuje dwa ciągi do pliku i zamyka plik. Dane wyjściowe to plik o nazwie _wfopen_test.xml, który zawiera dane z sekcji wyjściowej.

```C
// crt__wfopen.c
// compile with: /W3
// This program creates a file (or overwrites one if
// it exists), in text mode using Unicode encoding.
// It then writes two strings into the file
// and then closes the file.

#include <stdio.h>
#include <stddef.h>
#include <stdlib.h>
#include <wchar.h>

#define BUFFER_SIZE 50

int main(int argc, char** argv)
{
    wchar_t str[BUFFER_SIZE];
    size_t  strSize;
    FILE*   fileHandle;

    // Create an the xml file in text and Unicode encoding mode.
    if ((fileHandle = _wfopen( L"_wfopen_test.xml",L"wt+,ccs=UNICODE")) == NULL) // C4996
    // Note: _wfopen is deprecated; consider using _wfopen_s instead
    {
        wprintf(L"_wfopen failed!\n");
        return(0);
    }

    // Write a string into the file.
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"<xmlTag>\n");
    strSize = wcslen(str);
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)
    {
        wprintf(L"fwrite failed!\n");
    }

    // Write a string into the file.
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"</xmlTag>");
    strSize = wcslen(str);
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)
    {
        wprintf(L"fwrite failed!\n");
    }

    // Close the file.
    if (fclose(fileHandle))
    {
        wprintf(L"fclose failed!\n");
    }
    return 0;
}
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
