---
title: "_fdopen —, _wfdopen — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fdopen
- _wfdopen
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
apitype: DLLExport
f1_keywords:
- _tfdopen
- _fdopen
- _wfdopen
- wfdopen
- tfdopen
dev_langs: C++
helpviewer_keywords:
- wfdopen function
- _fdopen function
- _wfdopen function
- tfdopen function
- fdopen function
- _tfdopen function
- streams, associating with files
ms.assetid: 262757ff-1e09-4472-a5b6-4325fc28f971
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7108fdedb2698e6065c22ebe6905d897ee389ece
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fdopen-wfdopen"></a>_fdopen, _wfdopen

Kojarzy strumienia z pliku, który został uprzednio otwarty dla we/wy niskiego poziomu.

## <a name="syntax"></a>Składnia

```c
FILE *_fdopen(
   int fd,
   const char *mode
);
FILE *_wfdopen(
   int fd,
   const wchar_t *mode
);
```

### <a name="parameters"></a>Parametry

*FD*  
Deskryptorów plików otwartych plików.

*Tryb*  
Typ dostępu do pliku.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik można otworzyć strumienia. Wartość wskaźnika o wartości null wskazuje błąd. Gdy wystąpi błąd, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ma ustawioną opcję `EBADF`, co oznacza deskryptor nieprawidłowego pliku lub `EINVAL`, co oznacza, że `mode` wskaźnika o wartości null został.

Aby uzyskać więcej informacji na temat tych i innych kodów błędów, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

`_fdopen` Funkcja kojarzy strumień we/wy z pliku, który jest identyfikowany przez *fd*i w związku z tym umożliwia pliku, który jest otwarty dla niskiego poziomu we/wy mają być buforowane i sformatowany. `_wfdopen`jest to wersja znaków dwubajtowych `_fdopen`; *tryb* argument `_wfdopen` jest ciągiem znaków dwubajtowych. `_wfdopen`i `_fdopen` w przeciwnym razie zachowują się tak samo.

Przekazany deskryptorów plików `_fdopen` należą do firmy przez zwróconego `FILE *` strumienia. Jeśli `_fdopen` zakończy się pomyślnie, nie należy wywoływać [ \_zamknąć](../../c-runtime-library/reference/close.md) na deskryptorów plików. Wywoływanie [fclose —](../../c-runtime-library/reference/fclose-fcloseall.md) w zwróconym `FILE *` również zamyka deskryptorów plików.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|\_UNICODE i \_nie zdefiniowano MBCS|\_Definicja MBCS|\_Definicja formatu UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_tfdopen`|`_fdopen`|`_fdopen`|`_wfdopen`|

*Tryb* ciąg znaków określa typ dostępu do pliku żądanie dla pliku:  

`"r"`  
Zostanie otwarty do odczytu. Jeśli plik nie istnieje lub nie można znaleźć, `fopen` wywołać kończy się niepowodzeniem.

`"w"`  
Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaną zniszczone.

`"a"`  
Zostanie otwarty do zapisu na końcu pliku (dołączanie). Tworzy plik, jeśli nie istnieje.

`"r+"`  
Otwiera odczytywanie i zapisywanie. (Plik musi istnieć).

`"w+"`  
Otwiera pusty plik na odczytywanie i zapisywanie. Jeśli dany plik istnieje, jego zawartość zostaną zniszczone.

`"a+"`  
Zostanie otwarty do odczytu i dołączenie kodu. Tworzy plik, jeśli nie istnieje.

Gdy plik jest otwarty z `"a"` lub `"a+"` dostęp typu zapis wszystkie operacje wykonywane na końcu pliku. Można można zmieniać ich położenia wskaźnika pliku przy użyciu `fseek` lub `rewind`, ale on jest zawsze przeniesiony z powrotem do koniec pliku przed żadnego zapisu, wykonywane są wymienione. W związku z tym nie można zastąpić istniejące dane. Gdy `"r+"`, `"w+"`, lub `"a+"` określono typ dostępu, odczytywanie i zapisywanie są dozwolone (plik jest określany jako otwarte dla "update"). Jednak podczas przełączania się między odczytu i zapisu, musi być aktywne `fflush`, `fsetpos`, `fseek`, lub `rewind` operacji. Można określić bieżącego położenia dla `fsetpos` lub `fseek` operacji, jeśli chcesz.

Oprócz powyższych wartości następujących znaków można również uwzględnić w *tryb* Aby określić tryb tłumaczenia na znaki nowego wiersza:

`t`  
Otwórz w tekście (translacji) trybu. W tym trybie karetki kombinacji powrotu wiersza kanału informacyjnego (CR LF) są przekształcane na jeden wiersz źródła (LF) na dane wejściowe, a LF znaki są tłumaczone na kombinacje CR LF w danych wyjściowych. Ponadto Ctrl + Z jest interpretowany jako plik końcowy znak wejściowy. W plikach otwarty do odczytu/zapisu `fopen` wyszukuje klawisze Ctrl + Z końcem pliku i usuwa go, jeśli to możliwe. Odbywa się, ponieważ używa `fseek` i `ftell` funkcji, aby przenieść w pliku, który kończy się wyrazem Ctrl + Z może spowodować `fseek` będzie działać nieprawidłowo zbliża się koniec pliku.

`b`  
Otwórz w trybie binarnym (niezrozumiały). Żadnych tłumaczeń z `t` tryb są pomijane.

`c`  
Włącz flagę zatwierdzeń skojarzonych z nim `filename` tak, aby zawartość buforów plików są zapisywane bezpośrednio na dysku, jeśli dowolny `fflush` lub `_flushall` jest wywoływana.

`n`  
Resetuj flagi zatwierdzeń skojarzonych z nim `filename` na "nie zatwierdzanie." Domyślnie włączone. Zastępuje ona również flagi globalne zatwierdzenia, gdy łącze programu z Commode.obj. Domyślnie flagi globalne zatwierdzania jest "nie-commit", chyba że zostaną jawnie połączone z programem z Commode.obj.

`t`, `c`, I `n` *tryb* opcje są rozszerzenia Microsoft do `fopen` i `_fdopen`. Nie należy ich używać, jeśli chcesz zachować przenośność ANSI.

Jeśli `t` lub `b` nie została podana w *tryb*, domyślny tryb tłumaczenia jest definiowana za pomocą zmiennej globalnej [ \_fmode —](../../c-runtime-library/fmode.md). Jeśli `t` lub `b` jest prefiksem do argumentu funkcji kończy się niepowodzeniem i zwraca wartość NULL. Omówienie trybach tekstowym i binarnym, zobacz [tekstu i we/wy binarne trybu pliku](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Prawidłowe znaki *tryb* parametry używane w `fopen` i `_fdopen` odpowiadają *oflag* argumenty użyte w [ \_Otwórz](../../c-runtime-library/reference/open-wopen.md) i [ \_sopen —](../../c-runtime-library/reference/sopen-wsopen.md), jak pokazano w poniższej tabeli:

|Znaki w *tryb* ciągu|Odpowiednik *oflag* wartość `_open` i`_sopen`|
|---------------------------------|---------------------------------------------------|
|`a`|**\_O\_WRONLY &#124; \_O\_APPEND** (zazwyczaj  **\_O\_WRONLY &#124; \_O\_tworzenie &#124; \_O\_APPEND**)|
|`a+`|**\_O\_RDWR &#124; \_O\_APPEND** (zazwyczaj  **\_O\_RDWR &#124; \_O\_APPEND &#124; \_O\_tworzenie** )|
|`r`|**\_O\_RDONLY**|
|`r+`|**\_O\_RDWR**|
|`w`|**\_O\_WRONLY** (zazwyczaj  **\_O\_WRONLY &#124; \_O\_tworzenie &#124; \_O\_TRUNC**)|
|`w+`|**\_O\_RDWR** (zazwyczaj  **\_O\_RDWR &#124; \_O\_tworzenie &#124; \_O\_TRUNC**)|
|`b`|**\_O\_BINARNE**|
|`t`|**\_O\_TEKSTU**|
|`c`|Brak|
|`n`|Brak|

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|`_fdopen`|\<stdio.h >|
|`_wfdopen`|\<stdio.h > lub \<wchar.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```c
// crt_fdopen.c
// This program opens a file by using low-level
// I/O, then uses _fdopen to switch to stream
// access. It counts the lines in the file.

#include <stdlib.h>
#include <stdio.h>
#include <fcntl.h>
#include <io.h>
#include <share.h>

int main( void )
{
   FILE *stream;
   int  fd, count = 0;
   char inbuf[128];

   // Open a file.
   if( _sopen_s( &fd, "crt_fdopen.txt", _O_RDONLY, _SH_DENYNO, 0 ) )
      exit( 1 );

   // Get stream from file descriptor.
   if( (stream = _fdopen( fd, "r" )) == NULL )
      exit( 1 );

   while( fgets( inbuf, 128, stream ) != NULL )
      count++;

   // After _fdopen, close by using fclose, not _close.
   fclose( stream );
   printf( "Lines in file: %d\n", count );
}
```

### <a name="input-crtfdopentxt"></a>Dane wejściowe: crt_fdopen.txt

```
Line one
Line two
```

### <a name="output"></a>Dane wyjściowe

```
Lines in file: 2
```

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
[\_Dup, \_dup2 —](../../c-runtime-library/reference/dup-dup2.md)   
[fclose —, \_fcloseall —](../../c-runtime-library/reference/fclose-fcloseall.md)   
[fopen —, \_wfopen —](../../c-runtime-library/reference/fopen-wfopen.md)   
[freopen —, \_wfreopen —](../../c-runtime-library/reference/freopen-wfreopen.md)   
[\_Otwórz, \_wopen —](../../c-runtime-library/reference/open-wopen.md)
