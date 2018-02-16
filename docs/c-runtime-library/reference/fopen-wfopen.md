---
title: "fopen —, _wfopen — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- opening files, for file I/O
- wfopen function
- tfopen function
- _tfopen function
- _wfopen function
- files [C++], opening
- fopen function
ms.assetid: e868993f-738c-4920-b5e4-d8f2f41f933d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5619aa0db0c7905ec62fef31f5aa0cc25fae8924
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="fopen-wfopen"></a>fopen, _wfopen
Otwiera plik. Bardziej bezpiecznych wersje tych funkcji, wykonujących kody błędów weryfikacji i przywracać dodatkowy parametr są dostępne; zobacz [fopen_s —, _wfopen_s —](../../c-runtime-library/reference/fopen-s-wfopen-s.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
FILE *fopen(   
   const char *filename,  
   const char *mode   
);  
FILE *_wfopen(   
   const wchar_t *filename,  
   const wchar_t *mode   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Nazwa pliku.  
  
 `mode`  
 Rodzaj dostępu, który jest włączony.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda z tych funkcji zwraca wskaźnik do otwartego pliku. Wartość wskaźnika o wartości null wskazuje błąd. Jeśli `filename` lub `mode` jest `NULL` pusty ciąg, te funkcje wyzwalacza obsługi nieprawidłowy parametr, który jest opisany w lub [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają `NULL` i ustaw `errno` do `EINVAL`.  
  
 Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `fopen` Funkcja otwiera plik, który jest określony przez `filename`. Domyślnie wąskimi `filename` ciąg jest interpretowany za pomocą strony kodowej ANSI (CP_ACP). W aplikacjach pulpitu systemu Windows można to zmienić na stronę kodową OEM (CP_OEMCP) przy użyciu [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534\(v=vs.85\).aspx) funkcji. Można użyć [AreFileApisANSI](https://msdn.microsoft.com/library/windows/desktop/aa363781\(v=vs.85\).aspx) funkcji, aby określić, czy `filename` jest interpretowany za pomocą ANSI lub OEM domyślna systemowa strona kodowa. `_wfopen` jest to wersja znaków dwubajtowych `fopen`; argumenty `_wfopen` są ciągami znaków dwubajtowych. W przeciwnym razie `_wfopen` i `fopen` zachowują się tak samo. Tylko przy użyciu `_wfopen` nie ma wpływu na zestaw znaków kodowane, który jest używany w strumieniu plików.  
  
 `fopen` akceptuje ścieżek, które są prawidłowe w systemie plików w punkcie wykonywania; `fopen` akceptuje ścieżki UNC ani ścieżki, obejmujących zamapowane dyski sieciowe, tak długo, jak system, który wykonuje kod ma dostęp do udziału lub mapowany dysk w czasie wykonywania. Podczas konstruowania ścieżki `fopen`, upewnij się, że dyski, ścieżki lub udziały sieciowe będą dostępne w środowisku wykonywania. Możesz użyć ukośnikami (/) lub ukośników odwrotnych (\\) jako separatorów katalog w ścieżce.  
  
 Zawsze sprawdzić wartość zwrotną, aby zobaczyć, czy wskaźnik ma wartość NULL, zanim będzie wykonywać żadnych dodatkowych operacji na pliku. Jeśli wystąpi błąd, zmiennej globalnej `errno` ustawiono i może zostać użyty do uzyskania informacji o określonych błędach. Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="unicode-support"></a>Obsługa formatu Unicode  
 `fopen` obsługuje strumienie pliku Unicode. Aby otworzyć plik Unicode, należy przekazać `ccs` Flaga, która określa żądaną kodowanie `fopen`, wykonując następujące czynności.  
  
 `FILE *fp = fopen("newfile.txt", "rt+, ccs=encoding");`  
  
 Dozwolone wartości `encoding` są `UNICODE`, `UTF-8`, i `UTF-16LE`.  
  
 Gdy plik jest otwarty w trybie Unicode, funkcji wejściowych tłumaczenie dane, które jest do odczytu z pliku do przechowywane jako typ danych UTF-16 `wchar_t`. Funkcje zapisu w pliku otwartym w trybie Unicode oczekiwać buforów, które zawierają dane UTF-16, przechowywane jako typ `wchar_t`. Jeśli plik jest zakodowany jako UTF-8, UTF-16 dane są tłumaczone na UTF-8 gdy jest ona zapisywana i pliku algorytmem UTF-8 zawartości jest przekształcana na UTF-16, została przeczytana. Próba odczytu lub zapisu nieparzystą liczbę bajtów w przyczyny tryb Unicode [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) błędu. Do odczytu lub zapisu danych przechowywanych w programie jako UTF-8, tryb tekstowe lub binarne pliku zamiast trybu Unicode. Ponosisz odpowiedzialność za wszelkie wymagane tłumaczenia kodowania.  
  
 Jeśli plik już istnieje i jest otwarty do odczytu lub dołączania, Byte kolejności znaku (BOM), jeśli znajdujących się w pliku Określa kodowanie. Kodowanie BOM pierwszeństwo nad kodowanie określonym przez `ccs` flagi. `ccs` Kodowanie jest używana tylko podczas BOM nie jest obecny lub plik jest nowy plik.  
  
> [!NOTE]
>  Wykrywanie BOM ma zastosowanie tylko do plików, które będą otwierane w trybie Unicode (to znaczy przez przekazanie `ccs` flagi).  
  
 Poniższa tabela zawiera podsumowanie tryby, które są używane dla różnych `ccs` flagi nadawane `fopen` i znaczniki kolejności bajtów w pliku.  
  
### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Na podstawie używane kodowanie ccs flagę i BOM  
  
|`ccs` Flaga|Nie BOM (lub nowy plik)|BOM: UTF-8|BOM: UTF-16|  
|----------------|----------------------------|-----------------|------------------|  
|`UNICODE`|`UTF-16LE`|`UTF-8`|`UTF-16LE`|  
|`UTF-8`|`UTF-8`|`UTF-8`|`UTF-16LE`|  
|`UTF-16LE`|`UTF-16LE`|`UTF-8`|`UTF-16LE`|  
  
 Pliki otwarty do zapisu w trybie Unicode mają BOM automatycznie zapisywane do nich.  
  
 Jeśli `mode` jest "`a, ccs=<encoding>`", `fopen` najpierw spróbuje otworzyć plik, używając odczytu i zapisu. Jeśli to się powiedzie, funkcja odczytuje BOM, aby określić kodowanie pliku; Jeśli to się nie powiedzie, funkcja używa domyślne kodowanie używane do pliku. W obu przypadkach `fopen` zostanie następnie otwórz ponownie plik przy użyciu dostęp tylko do zapisu. (Dotyczy to `a` tryb tylko nie `a+` trybu.)  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tfopen`|`fopen`|`fopen`|`_wfopen`|  
  
 Ciąg znaków `mode` określa rodzaj dostępu do żądanego pliku, w następujący sposób.  
  
 `"r"`  
 Zostanie otwarty do odczytu. Jeśli plik nie istnieje lub nie można znaleźć, `fopen` wywołać kończy się niepowodzeniem.  
  
 `"w"`  
 Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaną zniszczone.  
  
 `"a"`  
 Zostanie otwarty do zapisu na końcu pliku (dołączanie) bez usuwania znacznika końca pliku (EOF), zanim nowe dane zostają zapisane do pliku. Tworzy plik, jeśli nie istnieje.  
  
 `"r+"`  
 Otwiera odczytywanie i zapisywanie. Plik musi istnieć.  
  
 `"w+"`  
 Otwiera pusty plik na odczytywanie i zapisywanie. Jeśli plik istnieje, jego zawartość zostaną zniszczone.  
  
 `"a+"`  
 Zostanie otwarty do odczytu i dołączenie kodu. Dołączanie operacja obejmuje usunięcie znacznik EOF przed nowe dane zostają zapisane do pliku. Znacznik EOF nie jest przywracany po zakończeniu zapisu. Tworzy plik, jeśli nie istnieje.  
  
 Gdy plik jest otwarty przy użyciu `"a"` dostęp typu lub `"a+"` dostęp typu, zapisać wszystkie operacje wykonywane na końcu pliku. Wskaźnika pliku można położenia przy użyciu `fseek` lub `rewind`, ale jest zawsze przeniesiony z powrotem na koniec pliku przed żadnego zapisu operacja została wykonana. W związku z tym nie można zastąpić istniejące dane.  
  
 `"a"` Trybu nie powoduje usunięcia znacznik EOF przed dołącza go do pliku. Po wystąpił dołączanie polecenia typu MS-DOS przedstawia tylko dane do oryginalnego znacznik EOF i nie dołączane do pliku. Przed dołącza go do pliku, `"a+"` tryb, usuń znacznik EOF. Po dołączeniu, polecenie typu MS-DOS Wyświetla wszystkie dane w pliku. `"a+"` Tryb jest wymagany do dołączenia do pliku strumienia, który kończy się znakiem znacznik EOF CTRL + Z.  
  
 Gdy `"r+"`, `"w+"`, lub `"a+"` określono typ dostępu, odczytywanie i zapisywanie są włączone (plik jest określany jako otwarte dla "update"). Jednak po przełączeniu odczytu do zapisu operacji wejściowy musi wystąpić znacznik EOF. Jeśli nie ma żadnych EOF, należy użyć pośredniczące wywołania do pliku pozycjonowanie funkcji. Funkcje pozycjonowania w pliku są `fsetpos`, `fseek`, i `rewind`. Po przełączeniu zapisywania do odczytu, musisz użyć wywołania pośredniczące `fflush` lub do pliku pozycjonowanie funkcji.  
  
 Oprócz wcześniej wartości następujących znaków można dołączać do `mode` Aby określić tryb tłumaczenia na znaki nowego wiersza.  
  
 `t`  
 Otwórz w tekście (translacji) trybu. W tym trybie CTRL + Z jest interpretowany jako znak EOF danych wejściowych. W plikach, które są otwarte do odczytu/zapisu przy użyciu `"a+"`, `fopen` wyszukuje klawisze CTRL + Z końcem pliku i usuwa go, jeśli jest to możliwe. Odbywa się, ponieważ używa `fseek` i `ftell` można przenieść w pliku, który może spowodować kończy się CTRL + Z `fseek` będzie działać nieprawidłowo zbliża się koniec pliku.  
  
 W trybie tekstowym kombinacji wysuwu wiersza powrotu karetki są przekształcane na pojedynczy znaki wysuwu wiersza na wejściu i wysuwu wiersza znaki są tłumaczone na kombinacje wysuwu wiersza powrotu karetki w danych wyjściowych. Jeśli funkcja strumienia I/O Unicode działa w trybie tekstowym (ustawienie domyślne), źródła lub strumień docelowy zakłada, że sekwencja znaków wielobajtowych. W związku z tym funkcji wejścia strumienia Unicode konwertuje znaki wielobajtowe na znaki dwubajtowe (tak jak w przypadku przez wywołanie do `mbtowc` funkcji). Z tego samego powodu funkcje strumieni wyjściowych Unicode przekonwertować znaki dwubajtowe znaków wielobajtowych (tak jak w przypadku przez wywołanie do `wctomb` funkcji).  
  
 `b`  
 Otwórz w trybie binarnym (niezrozumiały); Tłumaczenie obejmujące znaki powrotu karetki i wysuwu wiersza są pomijane.  
  
 Jeśli `t` lub `b` nie została podana w `mode`, domyślny tryb tłumaczenia jest definiowana za pomocą zmiennej globalnej [_fmode —](../../c-runtime-library/fmode.md). Jeśli `t` lub `b` jest prefiksem argument, funkcja kończy się niepowodzeniem i zwraca `NULL`.  
  
 Aby uzyskać więcej informacji na temat używania trybach tekstowym i binarnym Unicode i wielobajtowe strumienia I/O zobacz [tekstu i we/wy binarne trybu pliku](../../c-runtime-library/text-and-binary-mode-file-i-o.md) i [we/wy strumienia w Unicode w trybach tekstowym i binarnym](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).  
  
 `c`  
 Włącz flagę zatwierdzeń skojarzonych z nim `filename` tak, aby zawartość buforów plików są zapisywane bezpośrednio na dysku, jeśli dowolny `fflush` lub `_flushall` jest wywoływana.  
  
 `n`  
 Resetuj flagi zatwierdzeń skojarzonych z nim `filename` na "nie zatwierdzanie." Domyślnie włączone. Zastępuje ona również flagi globalne zatwierdzenia, gdy łącze programu z COMMODE.OBJ. Domyślnie flagi globalne zatwierdzania jest "nie-commit", chyba że zostaną jawnie połączone z programem z COMMODE. OBJ (zobacz [opcje łącza](../../c-runtime-library/link-options.md)).  
  
 `N`  
 Określa, że plik nie jest dziedziczona przez procesy podrzędne.  
  
 `S`  
 Określa, że buforowanie jest zoptymalizowana pod kątem, ale nie ograniczona do dostęp sekwencyjny z dysku.  
  
 `R`  
 Określa, że buforowanie jest zoptymalizowana pod kątem, ale nie ograniczona do dostępie swobodnym z dysku.  
  
 `T`  
 Określa plik jako tymczasowy. Jeśli to możliwe, nie jest opróżniany na dysku.  
  
 `D`  
 Określa plik jako tymczasowy. Jest ono usuwane po zamknięciu ostatniego wskaźnika pliku.  
  
 `ccs=ENCODING`  
 Określa używany zestaw znaków kodowane (`UTF-8`, `UTF-16LE`, lub `UNICODE`) dla tego pliku. Pozostaw nieokreślony, jeśli chcesz kodowania ANSI.  
  
 Prawidłowe znaki `mode` ciąg, który jest używany w `fopen` i `_fdopen` odpowiadają `oflag` argumenty, które są używane w [_otwórz](../../c-runtime-library/reference/open-wopen.md) i [_sopen —](../../c-runtime-library/reference/sopen-wsopen.md), wykonując następujące czynności.  
  
|Znaki w ciągu tryb|Odpowiednik `oflag` wartość `_open`/`_sopen`|  
|-------------------------------|----------------------------------------------------|  
|`a`|`_O_WRONLY &#124; _O_APPEND` (zazwyczaj `_O_WRONLY &#124; _O_CREAT &#124; _O_APPEND`)|  
|`a+`|`_O_RDWR &#124; _O_APPEND` (zazwyczaj `_O_RDWR &#124; _O_APPEND &#124; _O_CREAT` )|  
|`r`|`_O_RDONLY`|  
|`r+`|`_O_RDWR`|  
|`w`|`_O_WRONLY` (zazwyczaj `_O_WRONLY &#124; _O_CREAT &#124; _O_TRUNC`)|  
|`w+`|`_O_RDWR` (zazwyczaj `_O_RDWR &#124; _O_CREAT &#124; _O_TRUNC`)|  
|`b`|`_O_BINARY`|  
|`t`|`_O_TEXT`|  
|`c`|Brak|  
|`n`|Brak|  
|`S`|`_O_SEQUENTIAL`|  
|`R`|`_O_RANDOM`|  
|`T`|`_O_SHORTLIVED`|  
|`D`|`_O_TEMPORARY`|  
|`ccs=UNICODE`|`_O_WTEXT`|  
|`ccs=UTF-8`|`_O_UTF8`|  
|`ccs=UTF-16LE`|`_O_UTF16`|  
  
 Jeśli używasz `rb` tryb, bez portu kodu i oczekiwany odczyt większość dużego pliku lub nie są dane dotyczące wydajności sieci, warto również, czy do używania pamięci mapowane Win32 plików jako opcję.  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`fopen`|\<stdio.h>|  
|`_wfopen`|\<stdio.h > lub \<wchar.h >|  
  
 `_wfopen` to rozszerzenie firmy Microsoft. Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
 `c`, `n`, `t`, `S`, `R`, `T`, I `D` `mode` opcje są rozszerzenia Microsoft do `fopen` i `_fdopen` i nie powinna być używana w przypadku gdy Przenośność ANSI jest pożądane.  
  
## <a name="example"></a>Przykład  
 Następujący program otwiera dwa pliki.  Używa `fclose` zamknąć pierwszy plik i `_fcloseall` zamknięcie wszystkich pozostałych plików.  
  
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
  
## <a name="example"></a>Przykład  
 Następujący program tworzy plik (lub jeden zastępuje, jeśli istnieje), w trybie tekstowym mający kodowanie Unicode.  Następnie zapisuje dwa ciągi do pliku i zamyka plik. Dane wyjściowe są plik o nazwie _wfopen_test.xml, zawierający dane z sekcji danych wyjściowych.  
  
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
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [fclose —, _fcloseall —](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [_fdopen —, _wfdopen —](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [ferror —](../../c-runtime-library/reference/ferror.md)   
 [_fileno](../../c-runtime-library/reference/fileno.md)   
 [freopen —, _wfreopen —](../../c-runtime-library/reference/freopen-wfreopen.md)   
 [_otwórz, _wopen —](../../c-runtime-library/reference/open-wopen.md)   
 [_setmode —](../../c-runtime-library/reference/setmode.md)   
 [_sopen, _wsopen](../../c-runtime-library/reference/sopen-wsopen.md)