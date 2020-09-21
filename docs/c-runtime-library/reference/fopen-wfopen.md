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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: b7889009fe2de3c5256d6caf6cb5afa8792919c4
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743064"
---
# <a name="fopen-_wfopen"></a>fopen, _wfopen

Otwiera plik. Dostępne są bardziej bezpieczne wersje tych funkcji, które wykonują dodatkowe sprawdzanie poprawności parametrów i zwracanych kodów błędów. Zobacz [fopen_s, _wfopen_s](fopen-s-wfopen-s.md).

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

*wyst*<br/>
Rodzaj dostępnego dostępu.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do otwartego pliku. Wartość wskaźnika o wartości null wskazuje na błąd. Jeśli *Nazwa pliku* lub *tryb* ma **wartość null** lub jest pustym ciągiem, te funkcje wyzwalają procedurę obsługi nieprawidłowego parametru, która jest opisana w temacie [Walidacja parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **wartość null** i ustawiają **errno** na **EINVAL**.

Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **fopen** otwiera plik, który jest określony przez *filename*. Domyślnie ciąg wąskiej *nazwy pliku* jest interpretowany przy użyciu strony kodowej ANSI (CP_ACP). W aplikacjach klasycznych systemu Windows można zmienić na stronę kodową OEM (CP_OEMCP) za pomocą funkcji [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) . Można użyć funkcji [AreFileApisANSI](/windows/win32/api/fileapi/nf-fileapi-arefileapisansi) , aby określić, czy *Nazwa pliku* jest interpretowana przy użyciu ANSI lub domyślnej strony kodowej OEM systemu. **_wfopen** to dwubajtowa wersja **fopen**; argumenty do **_wfopen** są ciągami znaków dwubajtowych. W przeciwnym razie **_wfopen** i **fopen** zachowują się identycznie. Użycie **_wfopen** nie ma wpływu na zakodowany zestaw znaków używany w strumieniu pliku.

**fopen** akceptuje ścieżki, które są prawidłowe w systemie plików w punkcie wykonywania; **fopen** akceptuje ścieżki UNC i ścieżki, które obejmują zamapowane dyski sieciowe, tak długo, jak system, który wykonuje kod, ma dostęp do udziału lub dysku zamapowanego w czasie wykonywania. Podczas konstruowania ścieżek dla **fopen**upewnij się, że dyski, ścieżki lub udziały sieciowe będą dostępne w środowisku wykonawczym. Jako separatorów katalogów w ścieżce można użyć ukośników (/) lub ukośników odwrotnych ( \\ ).

Zawsze sprawdzaj wartość zwracaną, aby sprawdzić, czy wskaźnik ma wartość NULL przed wykonaniem jakichkolwiek dodatkowych operacji na pliku. Jeśli wystąpi błąd, zmienna globalna **errno** jest ustawiona i może służyć do uzyskiwania określonych informacji o błędzie. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="unicode-support"></a>Obsługa formatu Unicode

**fopen** obsługuje strumienie plików w formacie Unicode. Aby otworzyć plik w formacie Unicode, należy przekazać flagę **CCS** , która określa wymagane kodowanie do **fopen**w następujący sposób.

> **Plik \* FP = fopen ("newfile.txt", "RT +, CCS =**_Encoding_**");**

Dozwolone wartości *kodowania* to **Unicode**, **UTF-8**i **UTF-16LE**.

Gdy plik jest otwarty w trybie Unicode, funkcje wejściowe tłumaczą dane, które są odczytywane z pliku do danych UTF-16 przechowywanych jako typ **`wchar_t`** . Funkcje, które zapisują do pliku otwartego w trybie Unicode, oczekują buforów zawierających dane w formacie UTF-16 przechowywane jako typ **`wchar_t`** . Jeśli plik jest zakodowany jako UTF-8, dane UTF-16 są tłumaczone na UTF-8 podczas zapisywania, a zawartość zakodowana w formacie UTF-8 jest tłumaczona na UTF-16 podczas odczytywania. Próba odczytania lub zapisania nieparzystej liczby bajtów w trybie Unicode powoduje błąd [walidacji parametru](../../c-runtime-library/parameter-validation.md) . Aby odczytać lub zapisać dane, które są przechowywane w programie jako UTF-8, użyj trybu plików tekstowych lub binarnych zamiast trybu Unicode. Użytkownik jest odpowiedzialny za wszelkie wymagane tłumaczenia kodowania.

Jeśli plik już istnieje i jest otwarty do odczytu lub dołączania, znacznik kolejności bajtów (BOM), jeśli jest obecny w pliku, określa kodowanie. Kodowanie BOM ma pierwszeństwo przed kodowaniem, które jest określone przez flagę **CCS** . Kodowanie **CCS** jest używane tylko wtedy, gdy nie jest obecny BOM lub plik jest nowym plikiem.

> [!NOTE]
> Wykrywanie BOM ma zastosowanie tylko do plików, które są otwarte w trybie Unicode (czyli przez przekazanie flagi **CCS** ).

Poniższa tabela zawiera podsumowanie trybów, które są używane dla różnych flag **CCS** przyznanych **fopen** i znaczniki kolejności bajtów w pliku.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Kodowania używane na podstawie flagi CCS i BOM

|Flaga CCS|Brak BOM (lub nowy plik)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Pliki otwarte do pisania w trybie Unicode mają automatycznie zapisywany BOM.

Jeśli *tryb* to **"a, CCS =**_Encoding_**"**, **fopen** najpierw próbuje otworzyć plik, używając dostępu do odczytu i zapisu. Jeśli to się powiedzie, funkcja odczytuje BOM, aby określić kodowanie pliku. Jeśli to się nie powiedzie, funkcja używa domyślnego kodowania dla pliku. W obu przypadkach **fopen** następnie ponownie otworzy plik przy użyciu dostępu tylko do zapisu. (Dotyczy to tylko trybu **"a"** , a nie trybu **"a +"** ).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**fopen**|**fopen**|**_wfopen**|

*Tryb* ciągu znaków określa rodzaj dostępu żądanego dla pliku, w następujący sposób.

|*wyst*|Access|
|-|-|
| **®** | Otwiera do odczytu. Jeśli plik nie istnieje lub nie można go znaleźć, wywołanie **fopen** kończy się niepowodzeniem. |
| **k** | Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaje zniszczona. |
| **z** | Otwiera do zapisu na końcu pliku (dołączanie) bez usuwania znacznika końca pliku (EOF) przed zapisaniem nowych danych do pliku. Tworzy plik, jeśli nie istnieje. |
| **"r +"** | Otwiera zarówno do odczytu, jak i do zapisu. Plik musi istnieć. |
| **"w +"** | Otwiera pusty plik do odczytu i zapisu. Jeśli plik istnieje, jego zawartość zostaje zniszczona. |
| **"a +"** | Otwiera do odczytu i dołączania. Operacja dołączania obejmuje usunięcie znacznika EOF przed zapisaniem nowych danych w pliku. Znacznik EOF nie zostanie przywrócony po zakończeniu zapisywania. Tworzy plik, jeśli nie istnieje. |

Gdy plik jest otwierany przy użyciu typu dostępu **"a"** lub typu dostępu **"a +"** , wszystkie operacje zapisu są wykonywane na końcu pliku. Można zmienić położenie wskaźnika pliku przy użyciu [fseek](fseek-fseeki64.md) lub [przewijania do tyłu](rewind.md), ale jest on zawsze przenoszony z powrotem na koniec pliku przed wykonaniem jakiejkolwiek operacji zapisu. W związku z tym istniejące dane nie mogą być zastępowane.

Tryb **"a"** nie usuwa znacznika EOF przed dołączeniem do pliku. Po wystąpieniu operacji dołączania polecenie typu MS-DOS wyświetla tylko dane do oryginalnego znacznika EOF, a nie wszelkie dane dołączone do pliku. Przed dołączeniem do pliku, tryb **"a +"** powoduje usunięcie znacznika EOF. Po dołączeniu, polecenie MS-DOS TYPE wyświetla wszystkie dane w pliku. Tryb **"a +"** jest wymagany do dołączania do pliku strumienia, który jest zakończony przy użyciu znacznika z oznaczeniem EOF Ctrl + z.

Gdy jest określony typ dostępu **"r +"**, **"z +"** lub **"a +** ", włączane jest odczytywanie i zapisywanie (plik zostanie otwarty dla "Update"). Jednak podczas przełączania z odczytu do zapisu, operacja wejściowa musi napotkać znacznik EOF. Jeśli nie ma żadnych EOF, należy użyć wywołującego wywołania funkcji umieszczania plików. Funkcje pozycjonowania plików to **fsetpos**, [fseek](fseek-fseeki64.md)i [przewijania do tyłu](rewind.md). Podczas przełączania z zapisu do odczytu, należy użyć wywołania wywołującego do **fflush** lub funkcji pozycjonowania pliku.

Oprócz wcześniejszych wartości, można dołączyć do *trybu* , aby określić tryb tłumaczenia dla znaków nowego wiersza.

|modyfikator *trybu*|Tryb tłumaczenia|
|-|-|
| **&** | Otwórz w trybie tekst (przetłumaczony). |
| **b** | Otwórz w trybie binarnym (nieprzetłumaczony); Tłumaczenia obejmujące znaki powrotu karetki i wysuwu wiersza są pomijane. |

W trybie tekstowym klawisze CTRL + Z są interpretowane jako znak EOF na wejściu. W plikach, które są otwierane do odczytu/zapisu przy użyciu **"a +"**, **fopen** sprawdza, czy Ctrl + Z na końcu pliku i usuwa go, jeśli jest to możliwe. Dzieje się tak, ponieważ użycie [fseek](fseek-fseeki64.md) i **ftell** do przenoszenia w pliku, który kończy się za pomocą kombinacji klawiszy CTRL + z, może spowodować, że [fseek](fseek-fseeki64.md) zachowywać się niepoprawnie blisko końca pliku.

W trybie tekstowym kombinacje kanałów powrotu karetki są tłumaczone na pojedyncze linie informacyjne na wejściu, a znaki wysuwu wiersza są tłumaczone na kombinacje kanałów powrotu karetki liniowej w danych wyjściowych. Gdy funkcja strumienia Unicode we/wy działa w trybie tekstowym (wartość domyślna), zakłada się, że strumień źródłowy lub docelowy jest sekwencją znaków wielobajtowych. W związku z tym funkcje wejściowe strumienia Unicode konwertują znaki wielobajtowe na znaki szerokie (jak w przypadku wywołania funkcji **mbtowc** ). Z tego samego powodu funkcje strumienia Unicode-Output przekonwertują szerokie znaki na znaki wielobajtowe (jak w przypadku wywołania funkcji **wctomb** ).

Jeśli **t** lub **b** nie jest określony w *trybie*, domyślny tryb tłumaczenia jest definiowany przez zmienną globalną [_fmode](../../c-runtime-library/fmode.md). Jeśli **t** lub **b** jest poprzedzony argumentem, funkcja kończy się niepowodzeniem i zwraca **wartość null**.

Aby uzyskać więcej informacji na temat używania trybów tekstowych i binarnych w strumieniach Unicode i wielobajtowych — we/wy, zobacz [plik tekstowy i tryb binarny we/wy](../../c-runtime-library/text-and-binary-mode-file-i-o.md) i [strumienia Unicode/o w trybach tekstowych i binarnych](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Poniższe opcje można dołączyć do *trybu* , aby określić dodatkowe zachowania.

|modyfikator *trybu*|Zachowanie|
|-|-|
| **x** | Wymusza Niepowodzenie funkcji, jeśli *Nazwa pliku* już istnieje. Można go używać tylko ze specyfikatorami "w" lub "w +". |
| **s** | Włącz flagę zatwierdzania dla skojarzonej *nazwy pliku* , aby zawartość bufora plików była zapisywana bezpośrednio na dysk, jeśli zostanie wywołana **fflush** lub **_flushall** . |
| **Azotan** | Zresetuj flagę zatwierdzania dla skojarzonej *nazwy pliku* na wartość "No-Commit". Jest to opcja domyślna. Zastępuje ona również globalną flagę zatwierdzania w przypadku łączenia programu z TOWARami. OBJ. Globalna flaga zatwierdzania ma wartość "No-Commit", chyba że jawnie łączysz program z TOWARami. OBJ (zobacz [Opcje linku](../../c-runtime-library/link-options.md)). |
| **N** | Określa, że plik nie jest dziedziczony przez procesy podrzędne. |
| **S** | Określa, że buforowanie jest zoptymalizowane dla, ale nie ograniczone do, dostęp sekwencyjny z dysku. |
| **R** | Określa, że buforowanie jest zoptymalizowane dla, ale nie ograniczone do, losowy dostęp z dysku. |
| **T** | Określa plik jako tymczasowy. Jeśli to możliwe, nie jest opróżniony na dysk. |
| **Wykres** | Określa plik jako tymczasowy. Jest usuwany, gdy ostatni wskaźnik pliku jest zamknięty. |
| **CCS =**_kodowanie_ | Określa zestaw znaków kodowanych do użycia (jeden z **UTF-8**, **UTF-16LE**lub **Unicode**) dla tego pliku. Pozostaw nieokreślony, jeśli chcesz użyć kodowania ANSI. |

Prawidłowe znaki w ciągu *trybu* , który jest używany w **fopen** i **_fdopen** odpowiadają argumentom *Oflag* , które są używane w [_open](open-wopen.md) i [_sopen](sopen-wsopen.md)w następujący sposób.

|Znaki w ciągu *trybu*|Równoważna wartość *Oflag* dla elementu \_ Open/ \_ sopen|
|-------------------------------|----------------------------------------------------|
|**z**|** \_ O \_ WRONLY** &#124; ** \_ o \_ dołączenie** (zazwyczaj ** \_ O \_ WRONLY** &#124; ** \_ o \_ ** tworzenie &#124; ** \_ o \_ dołączeniu**)|
|**a +**|** \_ O \_ RDWR** &#124; ** \_ o \_ dołączenie** (zazwyczaj ** \_ O \_ RDWR** &#124; ** \_ o \_ dołączenie** &#124; ** \_ o \_ ** tworzenie)|
|**®**|**\_O \_ RDONLY**|
|**Język r +**|**\_O \_ RDWR**|
|**k**|** \_ O \_ WRONLY** (zazwyczaj ** \_ o \_ WRONLY** &#124; ** \_ o \_ ** &#124; ** \_ o \_ TRUNC —**)|
|**w +**|** \_ O \_ RDWR** (zazwyczaj ** \_ o \_ RDWR** &#124; ** \_ o \_ ** &#124; ** \_ o \_ TRUNC —**)|
|**b**|**\_O \_ plik binarny**|
|**&**|**\_O \_ tekst**|
|**x**|**\_O \_ bez**|
|**s**|Brak|
|**Azotan**|Brak|
|**S**|**\_O \_ sekwencyjnie**|
|**R**|**\_O \_ losowo**|
|**T**|**\_O \_ SHORTLIVED**|
|**Wykres**|**\_O \_ tymczasowych**|
|**CCS = UNICODE**|**\_O \_ WTEXT**|
|**CCS = UTF-8**|**\_O \_ UTF8**|
|**CCS = UTF-16LE**|**\_O \_ UTF16**|

W przypadku korzystania z trybu **RB** nie trzeba portować kodu, a jeśli oczekuje się, że większość dużego pliku lub nie dotyczy wydajności sieci, można również rozważyć, czy używać plików Win32 mapowanych w pamięci jako opcji.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fopen**|\<stdio.h>|
|**_wfopen**|\<stdio.h> lub \<wchar.h>|

**_wfopen** to rozszerzenie firmy Microsoft. Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

Opcje *trybu* **c**, **n**, **t**, **S**, **R**, **t**i **D** są rozszerzeniami firmy Microsoft dla **fopen** i **_fdopen** i nie powinny być używane w przypadku potrzeby przenoszenia w formacie ANSI.

## <a name="example-1"></a>Przykład 1

Poniższy program otwiera dwa pliki.  Używa **fclose** , aby zamknąć pierwszy plik i **_fcloseall** zamknąć wszystkie pozostałe pliki.

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

Następujący program tworzy plik (lub zastępuje go, jeśli istnieje) w trybie tekstowym, który ma kodowanie Unicode.  Następnie zapisuje dwa ciągi do pliku i zamyka plik. Dane wyjściowe to plik o nazwie _wfopen_test.xml, który zawiera dane z sekcji Output.

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
[Interpretacja sekwencji znaków wielobajtowych](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
