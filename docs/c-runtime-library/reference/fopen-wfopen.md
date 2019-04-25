---
title: fopen, _wfopen
ms.date: 11/04/2016
apiname:
- _wfopen
- fopen
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
ms.openlocfilehash: 9c7a7fed8eabc38f1a0a67587d495e75ba8fa3d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333342"
---
# <a name="fopen-wfopen"></a>fopen, _wfopen

Otwiera plik. Bardziej bezpieczne wersje tych funkcji, które wykonują kody błędów sprawdzania poprawności i zwrócenie dodatkowy parametr są dostępne; zobacz [fopen_s —, _wfopen_s —](fopen-s-wfopen-s.md).

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

*Nazwa pliku*<br/>
Nazwa pliku.

*Tryb*<br/>
Rodzaj dostępu, który jest włączony.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do otwartego pliku. Wartość null wskaźnika wskazuje na błąd. Jeśli *filename* lub *tryb* jest **NULL** lub pustym ciągiem, funkcje te wywołują nieprawidłowy parametr uchwytu, który jest opisany w [parametru Sprawdzanie poprawności](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **NULL** i ustaw **errno** do **EINVAL**.

Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**Fopen —** funkcja otwiera plik, który jest określony przez *filename*. Domyślnie zawęzić *filename* ciąg jest interpretowany przy użyciu strony kodowej ANSI (CP_ACP). W aplikacjach Windows Desktop można to zmienić stronę kodową OEM (CP_OEMCP) przy użyciu [SetFileApisToOEM](/windows/desktop/api/fileapi/nf-fileapi-setfileapistooem) funkcji. Możesz użyć [AreFileApisANSI](/windows/desktop/api/fileapi/nf-fileapi-arefileapisansi) funkcję, aby określić, czy *filename* jest interpretowany przy użyciu ANSI lub systemowa strona kodowa OEM domyślne. **_wfopen —** to wersja znaku dwubajtowego **fopen —**; argumenty **_wfopen —** są ciągami znaków dwubajtowych. W przeciwnym razie **_wfopen —** i **fopen —** zachowują się identycznie. Za pomocą adresu **_wfopen —** nie ma wpływu na kodowany zestaw znaków używany w strumieniu plików.

**fopen —** akceptuje ścieżki, które są prawidłowe w systemie plików w momencie wykonywania. **fopen —** akceptuje ścieżki UNC i ścieżki, które obejmują zamapowane dyski sieciowe, tak długo, jak system, w którym wykonywany jest kod ma dostęp do udziału lub mapowanego dysku sieciowego w czasie wykonywania. Podczas konstruowania ścieżek dla **fopen —**, upewnij się, że dyski, ścieżki lub udziały sieciowe będą dostępne w środowisku wykonawczym. Możesz użyć ukośnikami (/) lub ukośników odwrotnych (\\) jako separatora katalogów w ścieżce.

Zawsze sprawdzać zwracaną wartość, aby zobaczyć, czy wskaźnik ma wartość NULL, przed wykonaniem wszelkich dodatkowych operacji na pliku. Jeśli wystąpi błąd, zmienna globalna **errno** ustawiono i może służyć do uzyskiwania informacji o określonych błędach. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="unicode-support"></a>Obsługa formatu Unicode

**fopen —** obsługuje strumienie pliku Unicode. Aby otworzyć plik w formacie Unicode, należy przekazać **ccs** flagę, która określa wymagane kodowanie do **fopen —**, wykonując następujące czynności.

> **PLIK \*fp = fopen — ("NowyPlik.txt", "rt + ccs =**_kodowanie_**");**

Dozwolone wartości parametru *kodowanie* są **UNICODE**, **UTF-8**, i **UTF-16LE**.

Gdy plik zostanie otwarty w trybie Unicode, wprowadzania funkcji tłumaczenia danych, które są odczytywane z pliku w formacie UTF-16 — dane przechowywane jako typ **wchar_t**. Funkcje, które zapisu do pliku, który został otwarty w trybie Unicode oczekiwać buforów, które zawierają dane UTF-16 przechowywane jako typ **wchar_t**. Jeśli plik jest zakodowany w formacie UTF-8, UTF-16 dane są tłumaczone na UTF-8 są zapisywane, gdy algorytmem UTF-8 zawartości jest tłumaczony na UTF-16, została przeczytana. Podjęto próbę odczytu lub zapisu nieparzystą liczbę bajtów w trybie Unicode powoduje, że [Walidacja parametru](../../c-runtime-library/parameter-validation.md) błędu. Do odczytu lub zapisu danych przechowywanych w programach w formacie UTF-8, należy użyć trybu plików tekstowych lub binarnych zamiast trybie Unicode. Odpowiedzialność za wszelkie wymagane tłumaczenia kodowania.

Jeśli plik już istnieje i jest otwarty w celu odczytu lub dołączania, bajt kolejności znaku (BOM), jeśli jest obecny w pliku Określa kodowanie. Kodowanie znaku BOM ma pierwszeństwo nad kodowaniem, który jest określony przez **ccs** flagi. **Ccs** używane jest kodowanie tylko wtedy, gdy znak BOM nie jest obecny lub plik jest nowy plik.

> [!NOTE]
> Wykrywanie znaku BOM ma zastosowanie tylko do plików otwieranych w trybie Unicode (czyli przez przekazanie **ccs** flagi).

W poniższej tabeli podsumowano tryby, które są używane dla różnych **ccs** nadawanym **fopen —** i znaczniki kolejności bajtów w pliku.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Kodowania używane na podstawie ccs flagę i znaku BOM

|flagi ccs|Nie znaku BOM (lub nowy plik)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Pliki otwarte do pisania w trybie Unicode mają automatycznie zapisywany ich znak BOM.

Jeśli *tryb* jest **", ccs =**_kodowanie_**"**, **fopen —** po raz pierwszy próbuje otworzyć plik za pomocą odczytu oraz dostęp do zapisu. W przypadku powodzenia funkcja odczytuje znak BOM, aby określić kodowanie pliku. w przypadku niepowodzenia funkcja używa domyślnego kodowania pliku. W obu przypadkach **fopen —** zostanie następnie ponownie otwórz plik przy użyciu dostępu tylko do zapisu. (Dotyczy to **""** tryb tylko, aby nie **"+"** tryb.)

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**fopen —**|**fopen —**|**_wfopen**|

Ciąg znaków *tryb* określa rodzaj dostępu, który jest wnioskowany dla pliku, w następujący sposób.

|*Tryb*|Access|
|-|-|
| **"r"** | Otwiera do odczytu. Jeśli plik nie istnieje lub nie można odnaleźć **fopen —** wywołanie zakończy się niepowodzeniem. |
| **"w"** | Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaje zniszczona. |
| **"a"** | Zostanie otwarty do zapisu na końcu pliku (dołączanie) bez usuwania znacznika końca pliku (EOF), zanim nowe dane są zapisywane do pliku. Tworzy plik, jeśli nie istnieje. |
| **"r +"** | Otwiera Odczyt i zapis. Plik musi istnieć. |
| **"w +"** | Otwiera pusty plik Odczyt i zapis. Jeśli plik istnieje, jego zawartość zostaje zniszczona. |
| **"+"** | Otwiera do odczytu i dołączania. Operacja dołączania obejmuje usunięcie znacznika EOF, zanim nowe dane są zapisywane do pliku. Znacznik EOF nie jest przywracany po zakończeniu zapisu. Tworzy plik, jeśli nie istnieje. |

Po otwarciu pliku przy użyciu **""** dostęp typu lub **"+"** uzyskiwać dostępu do typu, wszystkie operacje zapisu występują na końcu pliku. Wskaźnik pliku może być przeniesiony za pomocą [fseek](fseek-fseeki64.md) lub [rewind](rewind.md), ale jest zawsze przenoszony z powrotem na koniec pliku przed wszelkie zapisu operacja została wykonana. W związku z tym nie można zastąpić istniejące dane.

**""** Trybu nie usuwa znacznika EOF przed wykonaniem do pliku. Po wystąpieniu operacji dołączania, polecenie MS-DOS TYPE pokazuje tylko dane przed oryginalnym znacznikiem EOF i nie żadnych danych dołączonych do pliku. Przed wykonaniem do pliku, **"+"** tryb usuwa znacznik EOF. Po operacji dołączania polecenie MS-DOS TYPE pokazuje wszystkie dane w pliku. **"+"** Tryb jest wymagany do wykonania operacji dołączania do pliku strumienia, który jest kończony przy użyciu CTRL + Z określającego znacznik EOF.

Gdy **"r +"**, **"w +"**, lub **"+"** jest określony typ dostępu, Odczyt i zapis są włączone (plik jest określany jako otwarty do "aktualizacji"). Jednak po przełączeniu z odczytu do zapisu operacja wprowadzania musi napotkać znacznik EOF. W przypadku znacznik EOF nie, należy użyć interwencyjnego wywołania funkcji położenia pliku. Funkcje położenia pliku to **fsetpos**, [fseek](fseek-fseeki64.md), i [rewind](rewind.md). Po przełączeniu się z zapisu do odczytu, należy użyć interwencyjnego wywołania **fflush —** lub funkcji położenia pliku.

Oprócz wcześniejszych wartości następujące znaki mogą być dołączane do *tryb* określić tryb translacji znaków nowego wiersza.

|*tryb* modyfikator|Tryb translacji|
|-|-|
| **t** | Otwórz w tekście (tłumaczonym) trybu. |
| **b** | Otwórz w trybie binarnym (nieprzetłumaczonym); tłumaczenia znaków powrotu karetki i wysuwu wiersza są pomijane. |

W trybie tekstowym CTRL + Z jest interpretowany jako znak końca pliku na dane wejściowe. W plikach otwartych do odczytu/zapisu, przy użyciu **"+"**, **fopen —** wyszukuje klawisze CTRL + Z na końcu pliku i usuwa go, jeśli jest to możliwe. Odbywa się, ponieważ używa [fseek](fseek-fseeki64.md) i **ftell —** można przenieść w pliku, który może spowodować, że kończy się znakiem CRTL + Z [fseek](fseek-fseeki64.md) będzie działać nieprawidłowo w pobliżu końca pliku.

W trybie tekstowym kombinacje wysuwu wiersza powrotu karetki są tłumaczone na jednym znaki wysuwu wiersza na dane wejściowe, a znaki wysuwu wiersza są tłumaczone na kombinacje wysuwu wiersza powrotu karetki na wyjściu. Kiedy funkcja strumienia we/wy Unicode działa w trybie tekstowym (ustawienie domyślne), źródło lub strumienia docelowego będzie traktowana jako sekwencja znaków wielobajtowych. W związku z tym, funkcje strumienia wejściowego Unicode konwertują znaki wielobajtowe do znaków dwubajtowych (tak jak w przypadku przez wywołanie **mbtowc** funkcji). Z tego samego powodu funkcje strumienia wyjściowego Unicode konwertują ciągi dwubajtowe na znaki wielobajtowe (tak jak w przypadku przez wywołanie **wctomb —** funkcji).

Jeśli **t** lub **b** nie jest podana w *tryb*, domyślny tryb translacji jest zdefiniowany przez zmienną globalną [_fmode](../../c-runtime-library/fmode.md). Jeśli **t** lub **b** jest umieszczany przez argument, funkcja kończy się niepowodzeniem i zwraca **NULL**.

Aby uzyskać więcej informacji o sposobie używania w trybach tekstowym i binarnym w Unicode i wielobajtowych strumienia we/wy, zobacz [tekstowych i binarnych We/Wy trybu](../../c-runtime-library/text-and-binary-mode-file-i-o.md) i [we/wy Stream w Unicode w trybach tekstowym i binarnym](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Poniższe opcje, które można dołączać do *tryb* Aby określić dodatkowe zachowania.

|*tryb* modyfikator|Zachowanie|
|-|-|
| **c** | Włącz flagę zatwierdzania dla skojarzonego *filename* tak, aby zawartość buforu pliku są zapisywane bezpośrednio na dysku, jeśli **fflush —** lub **_flushall —** jest wywoływana. |
| **n** | Resetowanie flagi zatwierdzenia dla skojarzonego *filename* do "no-commit". Domyślnie włączone. Zastępuje również globalną flagę zatwierdzania, jeśli łączysz się program jest połączony z plikiem COMMODE.OBJ. Domyślna globalnej flagi zatwierdzania to "no-commit", chyba że jawnie połączyć program jest połączony z COMMODE. OBJ (zobacz [opcje łącza](../../c-runtime-library/link-options.md)). |
| **N** | Określa, że plik nie jest dziedziczony przez procesy podrzędne. |
| **S** | Określa, że buforowanie jest zoptymalizowane pod kątem, ale nie ogranicza się do dostępu sekwencyjnego do dysku. |
| **R** | Określa, że buforowanie jest zoptymalizowane pod kątem, ale nie ogranicza się do dostępu losowego do dysku. |
| **T** | Określa plik jako tymczasowy. Jeśli to możliwe, nie jest on opróżniany do dysku. |
| **D** | Określa plik jako tymczasowy. Jest usuwany po zamknięciu ostatniego wskaźnika do pliku. |
| **ccs=**_encoding_ | Określa zakodowany zestaw znaków używany (jeden z **UTF-8**, **UTF-16LE**, lub **UNICODE**) dla tego pliku. Pozostaw nieokreślony, jeśli chcesz, aby kodowania ANSI. |

Prawidłowe znaki *tryb* ciąg, który jest używany w **fopen —** i **_fdopen —** odpowiadają *oflag* argumenty, które są używane w [_otwórz](open-wopen.md) i [_sopen](sopen-wsopen.md), wykonując następujące czynności.

|Znaki w *tryb* ciągu|Równoważne *oflag* wartość \_Otwórz /\_sopen —|
|-------------------------------|----------------------------------------------------|
|**a**|**\_O\_WRONLY** &#124;  **\_O\_APPEND** (zazwyczaj  **\_O\_WRONLY** &#124;  **\_O\_CREAT** &#124;  **\_O\_APPEND**)|
|**a+**|**\_O\_RDWR** &#124; **\_O\_APPEND** (usually **\_O\_RDWR** &#124; **\_O\_APPEND** &#124; **\_O\_CREAT** )|
|**r**|**\_O\_RDONLY**|
|**r+**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** (zazwyczaj  **\_O\_WRONLY** &#124;  **\_O\_CREAT** &#124;  **\_O\_TRUNC**)|
|**w +**|**\_O\_RDWR** (usually **\_O\_RDWR** &#124; **\_O\_CREAT** &#124; **\_O\_TRUNC**)|
|**b**|**\_O\_BINARY**|
|**t**|**\_O\_TEXT**|
|**c**|Brak|
|**n**|Brak|
|**S**|**\_O\_SEKWENCYJNEGO**|
|**R**|**\_O\_RANDOM**|
|**T**|**\_O\_SHORTLIVED**|
|**D**|**\_O\_TEMPORARY**|
|**ccs=UNICODE**|**\_O\_WTEXT**|
|**ccs=UTF-8**|**\_O\_UTF8**|
|**ccs=UTF-16LE**|**\_O\_UTF16**|

Jeśli używasz **rb** tryb, nie trzeba przyłącz kod, a jeśli chcą odczytywana większość dużego pliku lub nie jest istotna wydajność sieci, możesz też rozważyć, czy do użycia pamięci plików Win32 mapowanych jako opcję.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fopen —**|\<stdio.h>|
|**_wfopen**|\<stdio.h > lub \<wchar.h >|

**_wfopen —** jest rozszerzeniem firmy Microsoft. Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

**c**, **n**, **t**, **S**, **R**, **T**, i **D**  *tryb* opcje są rozszerzeniami firmy Microsoft dla **fopen —** i **_fdopen —** i nie powinna być używana gdzie pożądana jest przenośność kodowania ANSI.

## <a name="example-1"></a>Przykład 1

Następujący program otwiera dwa pliki.  Używa ona **fclose —** zamknąć pierwszy plik i **_fcloseall** zamknąć wszystkie pozostałe pliki.

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

Następujący program tworzy plik (lub zastępuje jeden, jeśli istnieje), w trybie tekstowym, który ma kodowanie Unicode.  Następnie zapisuje dwa ciągi w pliku i zamyka plik. Dane wyjściowe są w pliku o nazwie _wfopen_test.xml, który zawiera dane z sekcji wyjściowej.

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

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
