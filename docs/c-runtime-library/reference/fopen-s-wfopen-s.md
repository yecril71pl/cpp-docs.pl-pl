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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 80d04e75637cfab9795bf5dfb9da9786cf4ebd71
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346492"
---
# <a name="fopen_s-_wfopen_s"></a>fopen_s, _wfopen_s

Otwiera plik. Te wersje [fopen, _wfopen](fopen-wfopen.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*p Plik*<br/>
Wskaźnik do wskaźnika pliku, który otrzyma wskaźnik do otwartego pliku.

*Pod nazwą*<br/>
Pod nazwą.

*Tryb*<br/>
Dozwolony typ dostępu.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie; kod błędu w przypadku awarii. Więcej informacji na temat tych kodów błędów można znaleźć [w _doserrno, _sys_errlist i _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

### <a name="error-conditions"></a>Warunki błędu

|*p Plik*|*Pod nazwą*|*Tryb*|Wartość zwracana|Zawartość *pliku pFile*|
|-------------|----------------|------------|------------------|------------------------|
|**Null**|Wszelki|Wszelki|**Einval**|Niezmienione|
|Wszelki|**Null**|Wszelki|**Einval**|Niezmienione|
|Wszelki|Wszelki|**Null**|**Einval**|Niezmienione|

## <a name="remarks"></a>Uwagi

Pliki otwierane przez **fopen_s** i **_wfopen_s** nie są dostępne do udostępniciń. Jeśli chcesz, aby plik był udostępniany, użyj [_fsopen, _wfsopen](fsopen-wfsopen.md) ze stałą odpowiedniego trybu udostępniania — na przykład **_SH_DENYNO** do udostępniania odczytu/zapisu.

Funkcja **fopen_s** otwiera plik określony przez nazwę *pliku*. **_wfopen_s** jest szerokoznakową wersją **fopen_s**; argumenty, które **mają _wfopen_s,** to ciągi znaków o szerokich znakach. **_wfopen_s** i **fopen_s** zachowują się identycznie w przeciwnym razie.

**fopen_s** akceptuje ścieżki, które są prawidłowe w systemie plików w punkcie wykonania; Ścieżki UNC i ścieżki, które obejmują mapowane dyski sieciowe są akceptowane przez **fopen_s** tak długo, jak system, który wykonuje kod ma dostęp do udziału lub mapowane dysku sieciowego w momencie wykonywania. Podczas konstruowania ścieżek dla **fopen_s,** nie należy zakładać dostępności dysków, ścieżek lub udziałów sieciowych w środowisku wykonywania. Jako separatory katalogów w ścieżce można użyć\\ukośników (/) lub ukośników odwrotnych ( ) (

Te funkcje sprawdzają ich parametry. Jeśli *pFile*, *nazwa pliku*lub *tryb* jest wskaźnikiem null, te funkcje generują nieprawidłowy wyjątek parametru, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md).

Zawsze sprawdź wartość zwracaną, aby sprawdzić, czy funkcja powiodła się przed wykonaniem dalszych operacji w pliku. Jeśli wystąpi błąd, zwracany jest kod błędu i ustawiona jest zmienna globalna **errno.** Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="unicode-support"></a>Obsługa unicode

**fopen_s** obsługuje strumienie plików Unicode. Aby otworzyć nowy lub istniejący plik Unicode, przekaż flagę *ccs* określającą żądane kodowanie do **fopen_s:**

**fopen_s(&fp, "newfile.txt", "rw, ccs=**_kodowanie_**");**

Dozwolone wartości *kodowania* to **UNICODE**, **UTF-8**i **UTF-16LE**. Jeśli nie określono żadnej wartości *kodowania,* **fopen_s** używa kodowania ANSI.

Jeśli plik już istnieje i jest otwarty do odczytu lub dołączania, znak bom (Byte Order Mark), jeśli jest obecny w pliku, określa kodowanie. Kodowanie BOM ma pierwszeństwo przed kodowaniem określonym przez flagę *ccs.* Kodowanie *ccs* jest używane tylko wtedy, gdy nie ma BOM-u lub jeśli plik jest nowym plikiem.

> [!NOTE]
> Wykrywanie BOM dotyczy tylko plików otwieranych w trybie Unicode; oznacza to, że mijając flagę *ccs.*

W poniższej tabeli podsumowano tryby dla różnych flag *ccs,* które są podane do **fopen_s** i znaczników kolejności bajtów w pliku.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Kodowanie używane na podstawie flagi ccs i BOM

|flaga ccs|Brak BOM (lub nowego pliku)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**Unicode**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

Pliki otwierane do zapisu w trybie Unicode mają automatycznie zapisywany do nich BOM.

Jeśli *tryb* jest **"a, ccs =**_kodowanie_**",** **fopen_s** najpierw próbuje otworzyć plik z dostępem do odczytu i dostępu do zapisu. Jeśli się powiedzie, funkcja odczytuje BOM w celu określenia kodowania pliku; Jeśli nie powiedzie się, funkcja używa domyślnego kodowania pliku. W obu przypadkach **fopen_s** następnie ponownie otwiera plik z dostępem tylko do zapisu. (Dotyczy to tylko **trybu,** **a nie+**.)

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen_s**|**fopen_s**|**fopen_s**|**_wfopen_s**|

*Tryb* ciągu znaków określa rodzaj dostępu, który jest wymagany dla pliku, w następujący sposób.

|*Tryb*|Dostęp|
|-|-|
| **"r"** | Otwiera się do czytania. Jeśli plik nie istnieje lub nie można go odnaleźć, **wywołanie fopen_s** nie powiedzie się. |
| **"w"** | Otwiera pusty plik do zapisania. Jeśli dany plik istnieje, jego zawartość zostanie zniszczona. |
| **"a"** | Otwiera się do zapisu na końcu pliku (dołączanie) bez usuwania znacznika końca pliku (EOF) przed zapisaniem nowych danych w pliku. Tworzy plik, jeśli nie istnieje. |
| **"r+"** | Otwiera się zarówno do czytania, jak i pisania. Plik musi istnieć. |
| **"w+"** | Otwiera pusty plik do odczytu i zapisu. Jeśli plik istnieje, jego zawartość zostanie zniszczona. |
| **"a+"** | Otwiera do czytania i dołączania. Operacja dołączania obejmuje usunięcie znacznika EOF przed zapisaniem nowych danych w pliku. Znacznik EOF nie zostanie przywrócony po zakończeniu zapisu. Tworzy plik, jeśli nie istnieje. |

Gdy plik jest otwierany przy użyciu typu dostępu **"a"** lub **"a+",** wszystkie operacje zapisu występują na końcu pliku. Wskaźnik pliku można zmienić położenie za pomocą [fseek](fseek-fseeki64.md) lub [przewijania](rewind.md)do tyłu , ale zawsze jest przenoszony z powrotem na koniec pliku przed przeprowadzeniem jakiejkolwiek operacji zapisu, tak aby istniejące dane nie mogły zostać zastąpione.

Tryb **"a"** nie usuwa znacznika EOF przed dołączeniem do pliku. Po dołączeniu polecenie MS-DOS TYPE pokazuje tylko dane do oryginalnego znacznika EOF, a nie wszystkie dane, które są dołączane do pliku. Tryb **"a+"** usuwa znacznik EOF przed dołączeniem do pliku. Po dołączeniu polecenie MS-DOS TYPE pokazuje wszystkie dane w pliku. Tryb **"a+"** jest wymagany do dołączania do pliku strumienia, który jest zakończony za pomocą znacznika CTRL + Z EOF.

Po określeniu typu dostępu **"r+",** **"w+"** lub **"a+"** dozwolone jest zarówno odczyt, jak i zapis. (Mówi się, że plik jest otwarty dla "aktualizacji".) Jednak po przełączeniu z odczytu do zapisu, operacja wprowadzania musi napotkać znacznik EOF. Jeśli nie ma eof, należy użyć interweniującego wywołania funkcji pozycjonowania plików. Funkcje pozycjonowania plików to **fsetpos**, [fseek](fseek-fseeki64.md)i [przewijanie do tyłu.](rewind.md) Po przełączeniu się z zapisu do odczytu, należy użyć połączenia interweniującego albo **fflush** lub funkcji pozycjonowania plików.

Oprócz powyższych wartości w *trybie* można uwzględnić następujące znaki, aby określić tryb tłumaczenia dla znaków nowego rzędu:

|modyfikator *trybu*|Tryb tłumaczenia|
|-|-|
| **t** | Otwórz w trybie tekstowym (przetłumaczonym). |
| **B** | Otwarte w trybie binarnym (nieprzetłumaczonym); tłumaczenia obejmujące znaki powrotu karetki i wiersza są pomijane. |

W trybie tekstowym (przetłumaczonym) ctrl+Z jest interpretowany jako znak końca pliku na danych wejściowych. W plikach otwartych do odczytu/zapisu z **"a+"** **fopen_s** sprawdza, czy na końcu pliku znajduje się CTRL+Z i usuwa go, jeśli to możliwe. Dzieje się tak, ponieważ za pomocą [fseek](fseek-fseeki64.md) i **ftell** przenieść w pliku, który kończy się CTRL + Z, może spowodować [fseek](fseek-fseeki64.md) zachowywać się nieprawidłowo pod koniec pliku.

Ponadto w trybie tekstowym kombinacje posuwu wiersza powrotu karetki są tłumaczone na pojedyncze kanały informacyjne na danych wejściowych, a znaki posuwu wiersza są tłumaczone na kombinacje posuwu wiersza powrotu karetki na wyjściu. Gdy funkcja strumienia Unicode we/wy działa w trybie tekstowym (domyślnie), przyjmuje się, że strumień źródłowy lub docelowy jest sekwencją znaków wielobajtowych. W związku z tym funkcje wejścia strumieniowego Unicode konwertują znaki wielobajtowe na znaki szerokie (tak jakby przez wywołanie funkcji **mbtowc).** Z tego samego powodu funkcje wyjścia strumieniowego Unicode konwertują znaki szerokokątne na znaki wielobajtowe (tak jakby przez wywołanie funkcji **wctomb).**

Jeśli **t** lub **b** nie jest podany w *trybie,* domyślny tryb tłumaczenia jest zdefiniowany przez zmienną globalną [_fmode](../../c-runtime-library/fmode.md). Jeśli **argument jest** poprzedzony t lub **b,** funkcja kończy się niepowodzeniem i zwraca **wartość NULL**.

Aby uzyskać więcej informacji na temat używania tekstu i trybów binarnych w trybie Unicode i wielobajtowym strumieniu We/Wy, zobacz [We/Wy pliku tekstowego i binarnego oraz](../../c-runtime-library/text-and-binary-mode-file-i-o.md) [we/wy strumienia Unicode w trybach tekstowych i binarnych](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

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

Prawidłowe znaki ciągu *trybu* **używanego** w fopen_s i [_fdopen](fdopen-wfdopen.md) odpowiadają argumentom *oflag używanym* w [_open](open-wopen.md) i [_sopen](sopen-wsopen.md)w następujący sposób.

|Znaki w *ciągu trybu*|Równoważna wartość *oflag* dla _open/_sopen|
|-------------------------------|----------------------------------------------------|
|**A**|**_O_WRONLY** &#124; **_O_APPEND** (zwykle **_O_WRONLY** &#124; **_O_CREAT &#124;**** _O_APPEND**|
|**a+**|**_O_RDWR** **&#124; _O_APPEND** (zwykle **_O_RDWR &#124;** **_O_APPEND &#124;** _O_CREAT **&#124;)**|
|**R**|**_O_RDONLY**|
|**r+**|**_O_RDWR**|
|**W**|**_O_WRONLY** (zwykle **_O_WRONLY** **&#124; _O_CREAT &#124;**** _O_TRUNC**)|
|**w+**|**_O_RDWR** (zwykle **_O_RDWR** &#124; _O_CREAT &#124; **_O_CREAT** **_O_TRUNC)**|
|**B**|**_O_BINARY**|
|**t**|**_O_TEXT**|
|**C**|Brak|
|**N**|Brak|
|**S**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**ccs=UNICODE**|**_O_WTEXT**|
|**ccs=UTF-8**|**_O_UTF8**|
|**ccs=UTF-16LE**|**_O_UTF16**|

Jeśli używasz trybu **rb,** nie trzeba port kodu, i spodziewać się przeczytać dużo pliku i / lub nie dbają o wydajność sieci, pamięci mapowane pliki Win32 może być również opcja.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fopen_s**|\<stdio.h>|
|**_wfopen_s**|\<stdio.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

Opcje **trybu c**, **n**i **t** *t* są rozszerzeniami firmy Microsoft dla **fopen_s** i [_fdopen](fdopen-wfdopen.md) i nie powinny być używane tam, gdzie wymagana jest przenośność ANSI.

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
