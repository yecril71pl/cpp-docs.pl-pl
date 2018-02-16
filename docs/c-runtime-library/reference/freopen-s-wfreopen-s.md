---
title: "freopen_s —, _wfreopen_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wfreopen_s
- freopen_s
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
- freopen_s
- _tfreopen_s
- _wfreopen_s
dev_langs:
- C++
helpviewer_keywords:
- _tfreopen_s function
- _wfreopen_s function
- file pointers [C++], reassigning
- tfreopen_s function
- wfreopen_s function
- freopen_s function
ms.assetid: ad25a4da-6ad4-476b-a86d-660b221ca84d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a62165fee7ed54a7eeadf5f381945936bb441908
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="freopens-wfreopens"></a>freopen_s, _wfreopen_s
Ponownie przypisuje wskaźnika pliku. Te wersje programu [freopen —, _wfreopen —](../../c-runtime-library/reference/freopen-wfreopen.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t freopen(   
   FILE** pFile,  
   const char *path,  
   const char *mode,  
   FILE *stream   
);  
errno_t _wfreopen(   
   FILE** pFile,  
   const wchar_t *path,  
   const wchar_t *mode,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out] `pFile`  
 Wskaźnik do wskaźnika pliku dostarczanych przez wywołanie.  
  
 [in] `path`  
 Ścieżka do nowego pliku.  
  
 [in] `mode`  
 Dozwolonego typu dostępu.  
  
 [in] `stream`  
 Wskaźnik do `FILE` struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda z tych funkcji zwraca kod błędu. Jeśli wystąpi błąd, oryginalny plik jest zamknięty.  
  
## <a name="remarks"></a>Uwagi  
 `freopen_s` Funkcji spowoduje zamknięcie pliku, w obecnie skojarzony z `stream` i następuje zmiana przypisania `stream` do pliku określonego przez `path.` `_wfreopen_s` jest wersja znaków dwubajtowych `_freopen_s`; `path` i `mode` argumenty `_wfreopen_s` są ciągami znaków dwubajtowych. `_wfreopen_s` i `_freopen_s` zachowują się tak samo w przeciwnym razie wartość.  
  
 Jeśli dowolny z `pFile`, `path`, `mode`, lub `stream` są `NULL`, lub jeśli `path` jest pustym ciągiem, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL` i zwracać `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tfreopen_s`|`freopen_s`|`freopen_s`|`_wfreopen_s`|  
  
 `freopen_s` zwykle jest używana do przekierowania wstępnie otwarte pliki `stdin`, `stdout`, i `stderr` do plików określone przez użytkownika. Nowy plik skojarzony z `stream` jest otwierany z `mode`, która jest ciąg znaków określający typ dostępu do żądanego pliku, w następujący sposób:  
  
 `"r"`  
 Zostanie otwarty do odczytu. Jeśli plik nie istnieje lub nie można znaleźć, `freopen_s` wywołać kończy się niepowodzeniem.  
  
 `"w"`  
 Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaną zniszczone.  
  
 `"a"`  
 Zostanie otwarty do zapisu na końcu pliku (dołączanie), nie usuwając znacznik EOF przed zapisaniem nowych danych do pliku. Tworzy plik, jeśli nie istnieje.  
  
 `"r+"`  
 Otwiera odczytywanie i zapisywanie. (Plik musi istnieć).  
  
 `"w+"`  
 Otwiera pusty plik na odczytywanie i zapisywanie. Jeśli dany plik istnieje, jego zawartość zostaną zniszczone.  
  
 `"a+"`  
 Zostanie otwarty do odczytu i dołączenie; Dołączanie operacja obejmuje usunięcie znacznik EOF przed nowe dane zostają zapisane do pliku i znacznik EOF jest przywracany po zakończeniu zapisu; Tworzy plik, jeśli nie istnieje.  
  
 Użyj `"w"` i `"w+"` typy z ostrożnością, zgodnie z ich zniszczyć istniejące pliki.  
  
 Gdy plik jest otwarty z `"a"` lub `"a+"` dostęp typu zapis wszystkich operacji miejsce na końcu pliku. Mimo że może być położenia wskaźnika pliku przy użyciu `fseek` lub `rewind`, wskaźnika pliku jest zawsze przeniesiony z powrotem na koniec pliku przed żadnego zapisu, wykonywane są wymienione. W związku z tym nie można zastąpić istniejące dane.  
  
 `"a"` Trybu nie powoduje usunięcia znacznik EOF przed dołączeniem do pliku. Po wystąpił dołączanie polecenia typu MS-DOS przedstawia tylko dane do oryginalnego znacznik EOF i nie dołączane do pliku. `"a+"` Tryb, usuń znacznik EOF przed dołączeniem do pliku. Po dołączeniu, polecenie typu MS-DOS Wyświetla wszystkie dane w pliku. `"a+"` Tryb jest wymagany do dołączenia do pliku strumienia, który kończy się znakiem znacznik EOF CTRL + Z.  
  
 Gdy `"r+"`, `"w+",` lub `"a+"` określono typ dostępu, odczytywanie i zapisywanie są dozwolone (plik jest określany jako otwarte dla "update"). Jednak podczas przełączania się między odczytu i zapisu, musi być aktywne [fsetpos —](../../c-runtime-library/reference/fsetpos.md), [fseek](../../c-runtime-library/reference/fseek-fseeki64.md), lub [rewind](../../c-runtime-library/reference/rewind.md) operacji. Bieżąca pozycja można określić dla `fsetpos` lub `fseek` operacji, w razie potrzeby. Oprócz powyższych wartości jednego z następujących znaków może być zawarta w `mode` ciąg, aby określić tryb tłumaczenia dla nowych wierszy.  
  
 `t`  
 Otwórz w tekście (translacji) trybu; kombinacje powrotu wysuwu wiersza (CR LF) karetki są tłumaczone na znaki wysuwu wiersza pojedynczego (LF) w danych wejściowych; LF znaki są tłumaczone na kombinacje CR LF w danych wyjściowych. Ponadto CTRL + Z jest interpretowany jako plik końcowy znak wejściowy. W plikach otwarty do odczytu lub zapisu i odczytu z `"a+"`, biblioteki wykonawczej wyszukuje klawisze CTRL + Z końcem pliku i usuwa go, jeśli to możliwe. Jest to zrobić, ponieważ używa `fseek` i `ftell` można przenieść w pliku może spowodować `fseek` będzie działać nieprawidłowo zbliża się koniec pliku. `t` Opcja to rozszerzenie firmy Microsoft, które nie powinny być używane których przenośność ANSI jest potrzebne.  
  
 `b`  
 Otwórz w trybie binarnym (niezrozumiały); powyżej tłumaczenia są pomijane.  
  
 Jeśli `t` lub `b` nie została podana w `mode`, domyślny tryb tłumaczenia jest definiowana za pomocą zmiennej globalnej [_fmode —](../../c-runtime-library/fmode.md). Jeśli `t` lub `b` jest prefiksem argument, funkcja kończy się niepowodzeniem i zwraca `NULL`.  
  
 Omówienie trybach tekstowym i binarnym, zobacz [tekstu i we/wy binarne trybu pliku](../../c-runtime-library/text-and-binary-mode-file-i-o.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|  
|--------------|---------------------|  
|`freopen_s`|\<stdio.h>|  
|`_wfreopen_s`|\<stdio.h > lub \<wchar.h >|  
  
 Konsoli nie jest obsługiwane w aplikacjach systemu Windows platformy Uniwersalnej. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu —`stdin`, `stdout`, i `stderr`— muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w aplikacji platformy uniwersalnej systemu Windows. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_freopen_s.c  
// This program reassigns stderr to the file  
// named FREOPEN.OUT and writes a line to that file.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
FILE *stream;  
  
int main( void )  
{  
   errno_t err;  
   // Reassign "stderr" to "freopen.out":   
   err = freopen_s( &stream, "freopen.out", "w", stderr );  
  
   if( err != 0 )  
      fprintf( stdout, "error on freopen\n" );  
   else  
   {  
      fprintf( stdout, "successfully reassigned\n" ); fflush( stdout );  
      fprintf( stream, "This will go to the file 'freopen.out'\n" );  
      fclose( stream );  
   }  
   system( "type freopen.out" );  
}  
```  
  
```Output  
successfully reassigned  
This will go to the file 'freopen.out'  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [freopen —, _wfreopen —](../../c-runtime-library/reference/freopen-wfreopen.md)   
 [fclose —, _fcloseall —](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [_fdopen —, _wfdopen —](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [_fileno](../../c-runtime-library/reference/fileno.md)   
 [fopen —, _wfopen —](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_otwórz, _wopen —](../../c-runtime-library/reference/open-wopen.md)   
 [_setmode](../../c-runtime-library/reference/setmode.md)