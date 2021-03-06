---
title: fopen_s, _wfopen_s
ms.date: 4/2/2020
api_name:
- _wfopen_s
- fopen_s
- _o__wfopen_s
- _o_fopen_s
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
ms.openlocfilehash: a06191791132784740fa85ca45e23e8aaa56279e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914911"
---
# <a name="fopen_s-_wfopen_s"></a>fopen_s, _wfopen_s

Otwiera plik. Te wersje programu [fopen _wfopen](fopen-wfopen.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Wskaźnik do wskaźnika pliku, który będzie otrzymywał wskaźnik do otwartego pliku.

*Nazwa pliku*<br/>
Nazwa pliku.

*wyst*<br/>
Dozwolony typ dostępu.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli pomyślne; kod błędu w przypadku niepowodzenia. Aby uzyskać więcej informacji o tych kodach błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

### <a name="error-conditions"></a>Warunki błędów

|*pFile*|*Nazwa pliku*|*wyst*|Wartość zwracana|Zawartość *pfile*|
|-------------|----------------|------------|------------------|------------------------|
|**NULL**|ile|ile|**EINVAL**|bez zmian|
|ile|**NULL**|ile|**EINVAL**|bez zmian|
|ile|ile|**NULL**|**EINVAL**|bez zmian|

## <a name="remarks"></a>Uwagi

Pliki otwierane przez **fopen_s** i **_wfopen_s** nie mogą być współużytkowane. Jeśli wymagane jest udostępnienie pliku, należy użyć [_fsopen, _wfsopen](fsopen-wfsopen.md) z odpowiednim stałym trybem udostępniania, na przykład **_SH_DENYNO** do udostępniania do odczytu i zapisu.

Funkcja **fopen_s** otwiera plik, który jest określony przez *filename*. **_wfopen_s** to dwubajtowa wersja **fopen_s**; argumenty do **_wfopen_s** są ciągami znaków dwubajtowych. **_wfopen_s** i **fopen_s** zachowują się identycznie w inny sposób.

**fopen_s** akceptuje ścieżki, które są prawidłowe w systemie plików w punkcie wykonywania; Ścieżki UNC i ścieżki, które obejmują zamapowane dyski sieciowe, są akceptowane przez **fopen_s** tak długo, jak system, który wykonuje kod, ma dostęp do udziału lub zamapowanego dysku sieciowego w czasie wykonywania. Podczas konstruowania ścieżek dla **fopen_s**nie należy tworzyć założeń dotyczących dostępności dysków, ścieżek ani udziałów sieciowych w środowisku wykonawczym. Jako separatorów katalogów w ścieżce można użyć ukośników (/) lub ukośników odwrotnych (\\).

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *pfile*, *filename*lub *mode* jest wskaźnikiem typu null, te funkcje generują wyjątek nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md).

Zawsze sprawdzaj wartość zwracaną, aby sprawdzić, czy funkcja zakończyła się pomyślnie przed wykonaniem dalszych operacji na pliku. Jeśli wystąpi błąd, kod błędu jest zwracany, a zmienna globalna **errno** jest ustawiona. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="unicode-support"></a>Obsługa Unicode

**fopen_s** obsługuje strumienie plików w formacie Unicode. Aby otworzyć nowy lub istniejący plik Unicode, należy przekazać flagę *CCS* , która określa żądane kodowanie do **fopen_s**:

**fopen_s (&FP, "NewFile. txt", "RW, CCS =**_Encoding_**");**

Dozwolone wartości *kodowania* to **Unicode**, **UTF-8**i **UTF-16LE**. Jeśli nie określono wartości dla *kodowania*, **FOPEN_S** używa kodowania ANSI.

Jeśli plik już istnieje i jest otwarty do odczytu lub dołączania, znacznik kolejności bajtów (BOM), jeśli jest obecny w pliku, określa kodowanie. Kodowanie BOM ma pierwszeństwo przed kodowaniem, które jest określone przez flagę *CCS* . Kodowanie *CCS* jest używane tylko wtedy, gdy nie jest obecny BOM lub plik jest nowym plikiem.

> [!NOTE]
> BOM — wykrywanie ma zastosowanie tylko do plików, które są otwarte w trybie Unicode; oznacza to, przekazując flagę *CCS* .

Poniższa tabela zawiera podsumowanie trybów różnych flag *CCS* , które są nadawane **Fopen_s** i dla znaczników kolejności bajtów w pliku.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Kodowania używane na podstawie flagi CCS i BOM

|Flaga CCS|Brak BOM (lub nowy plik)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Pliki otwarte do pisania w trybie Unicode mają automatycznie zapisywany BOM.

Jeśli *tryb* ma **wartość "a, CCS =**_Encoding_**"**, **fopen_s** najpierw próbuje otworzyć plik z dostępem do odczytu i zapisu. Jeśli to się powiedzie, funkcja odczytuje BOM, aby określić kodowanie pliku. Jeśli to się nie powiedzie, funkcja używa domyślnego kodowania dla pliku. W obu przypadkach **fopen_s** następnie ponownie otwiera plik z dostępem tylko do zapisu. (Dotyczy **tylko trybu,** a nie **+**).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen_s**|**fopen_s**|**fopen_s**|**_wfopen_s**|

*Tryb* ciągu znaków określa rodzaj dostępu żądanego dla pliku, w następujący sposób.

|*wyst*|Dostęp|
|-|-|
| **®** | Otwiera do odczytu. Jeśli plik nie istnieje lub nie można go znaleźć, wywołanie **fopen_s** nie powiedzie się. |
| **k** | Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaje zniszczona. |
| **z** | Otwiera do zapisu na końcu pliku (dołączanie) bez usuwania znacznika końca pliku (EOF) przed zapisaniem nowych danych do pliku. Tworzy plik, jeśli nie istnieje. |
| **"r +"** | Otwiera zarówno do odczytu, jak i do zapisu. Plik musi istnieć. |
| **"w +"** | Otwiera pusty plik do odczytu i zapisu. Jeśli plik istnieje, jego zawartość zostaje zniszczona. |
| **"a +"** | Otwiera do odczytu i dołączania. Operacja dołączania obejmuje usunięcie znacznika EOF przed zapisaniem nowych danych w pliku. Znacznik EOF nie zostanie przywrócony po zakończeniu zapisywania. Tworzy plik, jeśli nie istnieje. |

Gdy plik jest otwierany przy użyciu typu dostępu **"a"** lub **"a +"** , wszystkie operacje zapisu są wykonywane na końcu pliku. Można zmienić położenie wskaźnika pliku przy użyciu [fseek](fseek-fseeki64.md) lub [przewijania do tyłu](rewind.md), ale jest on zawsze przenoszony z powrotem do końca pliku przed wykonaniem jakiejkolwiek operacji zapisu, aby nie można było zastąpić istniejących danych.

Tryb **"a"** nie usuwa znacznika EOF przed dołączeniem do pliku. Po wystąpieniu operacji dołączania polecenie typu MS-DOS wyświetla tylko dane do oryginalnego znacznika EOF, a nie wszelkie dane dołączone do pliku. Tryb **"a +"** powoduje usunięcie znacznika EOF przed dołączeniem do pliku. Po dołączeniu, polecenie MS-DOS TYPE wyświetla wszystkie dane w pliku. Tryb **"a +"** jest wymagany do dołączania do pliku strumienia, który jest zakończony przy użyciu znacznika z oznaczeniem EOF Ctrl + z.

W przypadku określenia typu dostępu **"r +"**, **"z +"** lub **"a +** " są dozwolone operacje odczytu i zapisu. (Plik jest otwarty dla "Update"). Jednak podczas przełączania z odczytu do zapisu, operacja wejściowa musi napotkać znacznik EOF. Jeśli nie ma żadnych EOF, należy użyć wywołania wywołującego do funkcji pozycjonowania plików. Funkcje położenia plików to **fsetpos**, [fseek](fseek-fseeki64.md)i [przewijania do tyłu](rewind.md). Podczas przełączania z zapisu do odczytu, należy użyć wywołania wywołującego do **fflush** lub funkcji pozycjonowania plików.

Oprócz powyższych wartości następujące znaki mogą być zawarte w *trybie* w celu określenia trybu tłumaczenia dla znaków nowego wiersza:

|modyfikator *trybu*|Tryb tłumaczenia|
|-|-|
| **&** | Otwórz w trybie tekst (przetłumaczony). |
| **b** | Otwórz w trybie binarnym (nieprzetłumaczony); Tłumaczenia obejmujące znaki powrotu karetki i wysuwu wiersza są pomijane. |

W trybie tekstu (tłumaczone) klawisze CTRL + Z są interpretowane jako znak końca pliku na wejściu. W pliku otwartym do odczytu/zapisu z **"a +"** **fopen_s** sprawdza, czy Ctrl + Z na końcu pliku i usuwa go, jeśli jest to możliwe. Dzieje się tak, ponieważ użycie [fseek](fseek-fseeki64.md) i **ftell** do przenoszenia w pliku, który kończy się na Ctrl + z, może spowodować, że [fseek](fseek-fseeki64.md) zachowywać się nieprawidłowo blisko końca pliku.

Ponadto w trybie tekstowym kombinacje kanałów powrotu karetki są tłumaczone na pojedyncze linie informacyjne w danych wejściowych, a znaki wysuwu wiersza są tłumaczone na kombinacje kanałów powrotu karetki liniowej w danych wyjściowych. Gdy funkcja strumienia Unicode we/wy działa w trybie tekstowym (wartość domyślna), zakłada się, że strumień źródłowy lub docelowy jest sekwencją znaków wielobajtowych. W związku z tym funkcje wejściowe strumienia Unicode konwertują znaki wielobajtowe na znaki szerokie (jak w przypadku wywołania funkcji **mbtowc** ). Z tego samego powodu funkcje strumienia Unicode-Output przekonwertują szerokie znaki na znaki wielobajtowe (jak w przypadku wywołania funkcji **wctomb** ).

Jeśli **t** lub **b** nie jest określony w *trybie*, domyślny tryb tłumaczenia jest definiowany przez zmienną globalną [_fmode](../../c-runtime-library/fmode.md). Jeśli **t** lub **b** jest poprzedzony argumentem, funkcja kończy się niepowodzeniem i zwraca **wartość null**.

Aby uzyskać więcej informacji na temat używania trybów tekstowych i binarnych w strumieniach Unicode i wielobajtowych — we/wy, zobacz [plik tekstowy i tryb binarny we/wy](../../c-runtime-library/text-and-binary-mode-file-i-o.md) i [strumienia Unicode/o w trybach tekstowych i binarnych](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

|modyfikator *trybu*|Zachowanie|
|-|-|
| **s** | Włącz flagę zatwierdzania dla skojarzonej *nazwy pliku* , aby zawartość bufora plików była zapisywana bezpośrednio na dysk, jeśli zostanie wywołana **fflush** lub **_flushall** . |
| **Azotan** | Zresetuj flagę zatwierdzania dla skojarzonej *nazwy pliku* na wartość "No-Commit". Domyślnie włączone. Zastępuje ona również globalną flagę zatwierdzania w przypadku łączenia programu z TOWARami. OBJ. Globalna flaga zatwierdzania ma wartość "No-Commit", chyba że jawnie łączysz program z TOWARami. OBJ (zobacz [Opcje linku](../../c-runtime-library/link-options.md)). |
| **Azotan** | Określa, że plik nie jest dziedziczony przez procesy podrzędne. |
| **S** | Określa, że buforowanie jest zoptymalizowane dla, ale nie ograniczone do, dostęp sekwencyjny z dysku. |
| **R** | Określa, że buforowanie jest zoptymalizowane dla, ale nie ograniczone do, losowy dostęp z dysku. |
| **T** | Określa plik jako tymczasowy. Jeśli to możliwe, nie jest opróżniony na dysk. |
| **Wykres** | Określa plik jako tymczasowy. Jest usuwany, gdy ostatni wskaźnik pliku jest zamknięty. |
| **CCS =**_kodowanie_ | Określa zestaw znaków kodowanych do użycia (jeden z **UTF-8**, **UTF-16LE**lub **Unicode**) dla tego pliku. Pozostaw nieokreślony, jeśli chcesz użyć kodowania ANSI. |

Prawidłowe znaki w ciągu *trybu* używane w **fopen_s** i [_fdopen](fdopen-wfdopen.md) odpowiadają argumentom *Oflag* używanym w [_open](open-wopen.md) i [_sopen](sopen-wsopen.md)w następujący sposób.

|Znaki w ciągu *trybu*|Równoważna wartość *Oflag* dla _open/_sopen|
|-------------------------------|----------------------------------------------------|
|**z**|**_O_WRONLY** &#124; **_O_APPEND** (zazwyczaj **_O_WRONLY** &#124; **_O_CREAT &#124; _O_APPEND** **)**|
|**a +**|**_O_RDWR** &#124; **_O_APPEND** (zazwyczaj **_O_RDWR** &#124; **_O_APPEND &#124; _O_CREAT** **)**|
|**®**|**_O_RDONLY**|
|**Język r +**|**_O_RDWR**|
|**k**|**_O_WRONLY** (zazwyczaj **_O_WRONLY** &#124; **_O_CREAT** &#124; **_O_TRUNC**)|
|**w +**|**_O_RDWR** (zazwyczaj **_O_RDWR** &#124; **_O_CREAT** &#124; **_O_TRUNC**)|
|**b**|**_O_BINARY**|
|**&**|**_O_TEXT**|
|**s**|Brak|
|**Azotan**|Brak|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**Wykres**|**_O_TEMPORARY**|
|**CCS = UNICODE**|**_O_WTEXT**|
|**CCS = UTF-8**|**_O_UTF8**|
|**CCS = UTF-16LE**|**_O_UTF16**|

W przypadku korzystania z trybu **RB** nie trzeba portować kodu i oczekujesz odczytania dużej ilości pliku i/lub nie należy uważać o wydajność sieci, ale pliki Win32 mapowane na pamięć mogą być również opcją.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fopen_s**|\<stdio. h>|
|**_wfopen_s**|\<stdio. h> lub \<WCHAR. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

Opcje **c**, **n**i **t** *mode* są rozszerzeniami Microsoft dla **fopen_s** i [_fdopen](fdopen-wfdopen.md) i nie powinny być używane w przypadku, gdy wymagana jest przenośność ANSI.

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

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
