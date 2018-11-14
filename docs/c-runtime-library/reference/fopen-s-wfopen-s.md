---
title: fopen_s, _wfopen_s
ms.date: 11/04/2016
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
ms.openlocfilehash: 1309f991b8251bde7d614aa274d8d2e9da7a8ed3
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51333354"
---
# <a name="fopens-wfopens"></a>fopen_s, _wfopen_s

Otwiera plik. Te wersje [fopen —, _wfopen —](fopen-wfopen.md) mają wzmocnienia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Dozwolony typ dostępu.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie; Kod błędu. Zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych kodów błędu.

### <a name="error-conditions"></a>Warunki błędów

|*pFile*|*Nazwa pliku*|*Tryb*|Wartość zwracana|Zawartość *pFile*|
|-------------|----------------|------------|------------------|------------------------|
|**NULL**|Wszystkie|Wszystkie|**EINVAL**|bez zmian|
|Wszystkie|**NULL**|Wszystkie|**EINVAL**|bez zmian|
|Wszystkie|Wszystkie|**NULL**|**EINVAL**|bez zmian|

## <a name="remarks"></a>Uwagi

Pliki, które są otwierane przez **fopen_s —** i **_wfopen_s —** nie są, które można udostępnić. Jeśli potrzebujesz, że można zabezpieczać pliku, użyj [_fsopen —, _wfsopen —](fsopen-wfsopen.md) z odpowiedniego udostępniania stałą tryb — na przykład **_SH_DENYNO** udostępniania odczytu/zapisu.

**Fopen_s —** funkcja otwiera plik, który jest określony przez *filename*. **_wfopen_s —** to wersja znaku dwubajtowego **fopen_s —**; argumenty **_wfopen_s —** są ciągami znaków dwubajtowych. **_wfopen_s —** i **fopen_s —** zachowują się identycznie.

**fopen_s —** akceptuje ścieżki, które są prawidłowe w systemie plików w momencie wykonywania. Ścieżki UNC i ścieżki, obejmujące zamapowane dyski sieciowe są akceptowane przez **fopen_s —** tak długo, jak system, który jest wykonywany kod ma dostęp do udziału lub zamapowany dysk sieciowy w czasie wykonywania. Podczas konstruowania ścieżek dla **fopen_s —**, nie wprowadzaj założeń dotyczących dostępności dysków, ścieżki lub udziały sieciowe w środowisku wykonawczym. Możesz użyć ukośnikami (/) lub ukośników odwrotnych (\\) jako separatora katalogów w ścieżce.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *pFile*, *filename*, lub *tryb* jest pustym wskaźnikiem, te funkcje tworzą wyjątek nieprawidłowego parametru, zgodnie z opisem w [Walidacja parametru ](../../c-runtime-library/parameter-validation.md).

Zawsze sprawdzać zwracaną wartość, aby zobaczyć, czy funkcja zakończyła się pomyślnie przed wykonaniem wszelkich dalszych operacji na pliku. Jeśli wystąpi błąd, zostanie zwrócony kod błędu i zmienna globalna **errno** jest ustawiona. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="unicode-support"></a>Obsługa formatu Unicode

**fopen_s —** obsługuje strumienie pliku Unicode. Aby otworzyć nowy lub istniejący plik w formacie Unicode, należy przekazać *ccs* flagę, która określa wymagane kodowanie do **fopen_s —**:

**fopen_s — (& fp, "NowyPlik.txt", "rw ccs =**_kodowanie_**");**

Dozwolone wartości parametru *kodowanie* są **UNICODE**, **UTF-8**, i **UTF-16LE**. Jeśli określono żadnej wartości dla *kodowanie*, **fopen_s —** przy użyciu kodowania ANSI.

Jeśli plik już istnieje i jest otwarty w celu odczytu lub dołączania, bajt kolejności znaku (BOM), jeśli jest obecny w pliku Określa kodowanie. Kodowanie znaku BOM ma pierwszeństwo nad kodowaniem, który jest określony przez *ccs* flagi. *Ccs* używane jest kodowanie tylko wtedy, gdy znak BOM nie jest obecny lub jeśli plik jest nowy plik.

> [!NOTE]
> Wykrywanie znaku BOM ma zastosowanie tylko do plików otwieranych w trybie Unicode; oznacza to przez przekazanie *ccs* flagi.

W poniższej tabeli podsumowano tryby dla różnych *ccs* flagi, które są określone na **fopen_s —** i znaczniki kolejności bajtów w pliku.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Kodowania używane na podstawie ccs flagę i znaku BOM

|flagi ccs|Nie znaku BOM (lub nowy plik)|BOM: UTF-8|ZNAK BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Pliki, które są otwarte do pisania w trybie Unicode mają automatycznie zapisywany ich znak BOM.

Jeśli *tryb* jest **", ccs =**_kodowanie_**"**, **fopen_s —** po raz pierwszy próbuje otworzyć plik z odczytu dostęp i dostęp do zapisu. W przypadku powodzenia funkcja odczytuje znak BOM, aby określić kodowanie pliku. w przypadku niepowodzenia funkcja używa domyślnego kodowania pliku. W obu przypadkach **fopen_s —** ponowne otwarcie pliku z dostępem tylko do zapisu. (Dotyczy to **a** nie tylko w trybie **a+**.)

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen_s —**|**fopen_s —**|**fopen_s —**|**_wfopen_s**|

Ciąg znaków *tryb* określa rodzaj dostępu, który jest wnioskowany dla pliku, w następujący sposób.

|*Tryb*|Access|
|-|-|
| **"r"** | Otwiera do odczytu. Jeśli plik nie istnieje lub nie można odnaleźć **fopen_s —** wywołanie zakończy się niepowodzeniem. |
| **"w"** | Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaje zniszczona. |
| **""** | Zostanie otwarty do zapisu na końcu pliku (dołączanie) bez usuwania znacznika końca pliku (EOF), zanim nowe dane są zapisywane do pliku. Tworzy plik, jeśli nie istnieje. |
| **"r +"** | Otwiera Odczyt i zapis. Plik musi istnieć. |
| **"w +"** | Otwiera pusty plik Odczyt i zapis. Jeśli plik istnieje, jego zawartość zostaje zniszczona. |
| **"+"** | Otwiera do odczytu i dołączania. Operacja dołączania obejmuje usunięcie znacznika EOF, zanim nowe dane są zapisywane do pliku. Znacznik EOF nie jest przywracany po zakończeniu zapisu. Tworzy plik, jeśli nie istnieje. |

Po otwarciu pliku przy użyciu **""** lub **"+"** uzyskiwać dostępu do typu, wszystkie operacje zapisu występują na końcu pliku. Wskaźnik pliku może być przeniesiony za pomocą [fseek](fseek-fseeki64.md) lub [rewind](rewind.md), ale on jest zawsze przenoszony z powrotem na koniec pliku przed wszelkie zapisu operacji odbywa się tak, aby nie można zastąpić istniejące dane.

**""** Trybu nie usuwa znacznika EOF przed dołączeniem do pliku. Po wystąpieniu operacji dołączania, polecenie MS-DOS TYPE pokazuje tylko dane przed oryginalnym znacznikiem EOF i nie wszystkie dane, które jest dołączany do pliku. **"+"** Tryb usuwa znacznika EOF przed dołączeniem do pliku. Po operacji dołączania polecenie MS-DOS TYPE pokazuje wszystkie dane w pliku. **"+"** Tryb jest wymagany do wykonania operacji dołączania do pliku strumienia, który jest kończony przy użyciu CTRL + Z określającego znacznik EOF.

Gdy **"r +"**, **"w +"**, lub **"+"** jest określony typ dostępu, Odczyt i zapis jest dozwolone. (Plik jest określany jako otwarty do "aktualizacji"). Jednak po przełączeniu z odczytu do zapisu operacja wprowadzania musi napotkać znacznik EOF. W przypadku znacznik EOF nie, należy użyć interwencyjnego wywołania funkcji położenia pliku. Funkcje położenia pliku to **fsetpos**, [fseek](fseek-fseeki64.md), i [rewind](rewind.md). Po przełączeniu się z zapisu do odczytu, należy użyć interwencyjnego wywołania **fflush —** lub funkcji położenia pliku.

Oprócz powyższych wartości następujące znaki mogą być zawarte w *tryb* określić tryb translacji znaków nowego wiersza:

|*tryb* modyfikator|Tryb translacji|
|-|-|
| **t** | Otwórz w tekście (tłumaczonym) trybu. |
| **b** | Otwórz w trybie binarnym (nieprzetłumaczonym); tłumaczenia znaków powrotu karetki i wysuwu wiersza są pomijane. |

W trybie tekstowym (tłumaczonym) CTRL + Z jest interpretowany jako znak końca pliku na wejściu. W przypadku plików otwartych do odczytu/zapisu z **"+"**, **fopen_s —** wyszukuje klawisze CTRL + Z końcem pliku i usuwa go, jeśli jest to możliwe. Odbywa się, ponieważ używa [fseek](fseek-fseeki64.md) i **ftell —** można przenieść w pliku, który kończy się znakiem CRTL + Z, może spowodować, że [fseek](fseek-fseeki64.md) działać nieprawidłowo w pobliżu końca pliku.

Ponadto w trybie tekstowym kombinacje wysuwu wiersza powrotu karetki są tłumaczone na jednym znaki wysuwu wiersza na dane wejściowe i znaki wysuwu wiersza są tłumaczone na kombinacje wysuwu wiersza powrotu karetki na wyjściu. Kiedy funkcja strumienia we/wy Unicode działa w trybie tekstowym (ustawienie domyślne), źródło lub strumienia docelowego będzie traktowana jako sekwencja znaków wielobajtowych. W związku z tym, funkcje strumienia wejściowego Unicode konwertują znaki wielobajtowe do znaków dwubajtowych (tak jak w przypadku przez wywołanie **mbtowc** funkcji). Z tego samego powodu funkcje strumienia wyjściowego Unicode konwertują ciągi dwubajtowe na znaki wielobajtowe (tak jak w przypadku przez wywołanie **wctomb —** funkcji).

Jeśli **t** lub **b** nie jest podana w *tryb*, domyślny tryb translacji jest zdefiniowany przez zmienną globalną [_fmode](../../c-runtime-library/fmode.md). Jeśli **t** lub **b** jest umieszczany przez argument, funkcja kończy się niepowodzeniem i zwraca **NULL**.

Aby uzyskać więcej informacji na temat używania w trybach tekstowym i binarnym w Unicode i wielobajtowych strumienia we/wy, zobacz [tekstowych i binarnych We/Wy trybu](../../c-runtime-library/text-and-binary-mode-file-i-o.md) i [we/wy Stream w Unicode w trybach tekstowym i binarnym](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

|*tryb* modyfikator|Zachowanie|
|-|-|
| **c** | Włącz flagę zatwierdzania dla skojarzonego *filename* tak, aby zawartość buforu pliku są zapisywane bezpośrednio na dysku, jeśli **fflush —** lub **_flushall —** jest wywoływana. |
| **N** | Resetowanie flagi zatwierdzenia dla skojarzonego *filename* do "no-commit". Domyślnie włączone. Zastępuje również globalną flagę zatwierdzania, jeśli łączysz się program jest połączony z plikiem COMMODE.OBJ. Domyślna globalnej flagi zatwierdzania to "no-commit", chyba że jawnie połączyć program jest połączony z COMMODE. OBJ (zobacz [opcje łącza](../../c-runtime-library/link-options.md)). |
| **N** | Określa, że plik nie jest dziedziczony przez procesy podrzędne. |
| **S** | Określa, że buforowanie jest zoptymalizowane pod kątem, ale nie ogranicza się do dostępu sekwencyjnego do dysku. |
| **R** | Określa, że buforowanie jest zoptymalizowane pod kątem, ale nie ogranicza się do dostępu losowego do dysku. |
| **T** | Określa plik jako tymczasowy. Jeśli to możliwe, nie jest on opróżniany do dysku. |
| **D** | Określa plik jako tymczasowy. Jest usuwany po zamknięciu ostatniego wskaźnika do pliku. |
| **ccs =**_kodowania_ | Określa zakodowany zestaw znaków używany (jeden z **UTF-8**, **UTF-16LE**, lub **UNICODE**) dla tego pliku. Pozostaw nieokreślony, jeśli chcesz, aby kodowania ANSI. |

Prawidłowe znaki *tryb* ciąg użyty w **fopen_s —** i [_fdopen —](fdopen-wfdopen.md) odpowiadają *oflag* argumenty używane w [_ Otwórz](open-wopen.md) i [_sopen](sopen-wsopen.md), wykonując następujące czynności.

|Znaki w *tryb* ciągu|Równoważne *oflag* wartość _otwórz/_sopen|
|-------------------------------|----------------------------------------------------|
|**a**|**_O_WRONLY** &#124; **_O_APPEND** (zazwyczaj **_O_WRONLY** &#124; **_O_CREAT** &#124;** _O_APPEND **)|
|**+**|**_O_RDWR** &#124; **_O_APPEND** (zazwyczaj **_O_RDWR** &#124; **_O_APPEND** &#124; **_O_CREAT** )|
|**r**|**_O_RDONLY**|
|**r +**|**_O_RDWR**|
|**w**|**_O_WRONLY** (zazwyczaj **_O_WRONLY** &#124; **_O_CREAT** &#124;** _O_TRUNC **)|
|**w +**|**_O_RDWR** (zazwyczaj **_O_RDWR** &#124; **_O_CREAT** &#124; **_O_TRUNC**)|
|**b**|**_O_BINARY**|
|**t**|**_O_TEXT**|
|**c**|Brak|
|**N**|Brak|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**ccs = UNICODE**|**_O_WTEXT**|
|**ccs = UTF-8**|**_O_UTF8**|
|**ccs = UTF-16LE**|**_O_UTF16**|

Jeśli używasz **rb** tryb, nie będzie konieczne przyłącz kod, a oczekiwany odczyt wiele pliku i/lub nie interesuje wydajność sieci, plików Win32 mapowanych w pamięci może być również opcję.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fopen_s —**|\<stdio.h>|
|**_wfopen_s**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

**c**, **n**, i **t** *tryb* opcje są rozszerzeniami firmy Microsoft dla **fopen_s —** i [_fdopen —](fdopen-wfdopen.md) i nie powinna być używana gdzie pożądana jest przenośność kodowania ANSI.

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

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
