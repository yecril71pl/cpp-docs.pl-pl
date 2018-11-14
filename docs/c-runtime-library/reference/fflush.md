---
title: fflush
ms.date: 11/04/2016
apiname:
- fflush
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
- fflush
helpviewer_keywords:
- streams, flushing
- flushing
- fflush function
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
ms.openlocfilehash: d03d20ee5024915d0ca4c5a21db4159e8c4f876a
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51329114"
---
# <a name="fflush"></a>fflush

Opróżnia strumienia.

## <a name="syntax"></a>Składnia

```C
int fflush(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Stream*<br/>
Wskaźnik do **pliku** struktury.

## <a name="return-value"></a>Wartość zwracana

**fflush —** zwraca wartość 0, jeśli bufor został pomyślnie opróżniony. Wartość 0 jest także zwracany w przypadkach, w których określonego strumienia ma bufor nie jest otwarty do odczytu tylko. Zwracana wartość wynosząca **EOF** wskazuje na błąd.

> [!NOTE]
> Jeśli **fflush —** zwraca **EOF**, dane mogły zostać utracone z powodu błędu zapisu. Podczas konfigurowania obsługi błąd krytyczny, jest najbezpieczniejszy wyłączyć buforowanie z **setvbuf —** funkcji lub użyć procedury we/wy niskiego poziomu, takich jak **_otwórz**, **_zamknij**, i **_write** zamiast funkcje We/Wy strumienia.

## <a name="remarks"></a>Uwagi

**Fflush —** funkcja opróżnia strumienia *strumienia*. Jeśli strumień został otwarty w zapisu trybu, lub został otwarty w trybie aktualizacji Ostatnia operacja została zapisu, zawartość buforu strumienia są zapisywane w pliku podstawowego lub urządzenie i rozmiar buforu jest odrzucany. Czy strumień został otwarty w trybie do odczytu, czy strumień został bez buforowania wywołanie **fflush —** nie ma wpływu, a wszelkie buforu są zachowywane. Wywołanie **fflush —** neguje efekt wszelkie wcześniejsze wywołanie elementu **ungetc —** dla strumienia. Strumień pozostaje otwarta po wywołaniu.

Jeśli *strumienia* jest **NULL**, zachowanie jest taka sama jak wywołanie **fflush —** na temat każdego strumienia open. Wszystkie strumienie otwarty w trybie zapisu, a wszystkie strumienie otwarte w trybie aktualizacji których ostatnia operacja zakończyła się zapis zostały przesłane. Wywołanie nie ma wpływu na innych strumieni.

Bufory są zazwyczaj obsługiwane przez system operacyjny, który określa optymalny czas automatycznie zapisywać dane na dysku: gdy bufor jest pełny, jeśli strumień jest zamknięty lub gdy program kończy się zwykle bez zamykania w strumieniu. Funkcja commit-to-disk biblioteki wykonawczej pozwala upewnić się, że krytyczne dane są zapisywane bezpośrednio na dysku, a nie do buforów systemu operacyjnego. Bez konieczności ponownego zapisu istniejący program, można włączyć tę funkcję, konsolidacji plików obiektu programu z plikiem COMMODE.OBJ. Wynikowy plik wykonywalny wywołuje w celu **_flushall —** zapisywanie zawartości wszystkich buforów na dysku. Tylko **_flushall —** i **fflush —** dotyczy plikiem COMMODE.OBJ.

Aby uzyskać informacje o sposobie sterowania funkcją commit-to-disk, zobacz [Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md), [fopen —](fopen-wfopen.md), i [_fdopen —](fdopen-wfdopen.md).

Ta funkcja blokuje wątek wywołujący i dlatego jest metodą o bezpiecznych wątkach. Dla wersji bez blokady, zobacz **_fflush_nolock —**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fflush**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fflush.c
#include <stdio.h>
#include <conio.h>

int main( void )
{
   int integer;
   char string[81];

   // Read each word as a string.
   printf( "Enter a sentence of four words with scanf: " );
   for( integer = 0; integer < 4; integer++ )
   {
      scanf_s( "%s", string, sizeof(string) );
      printf( "%s\n", string );
   }

   // You must flush the input buffer before using gets.
   // fflush on input stream is an extension to the C standard
   fflush( stdin );
   printf( "Enter the same sentence with gets: " );
   gets_s( string, sizeof(string) );
   printf( "%s\n", string );
}
```

```Input
This is a test
This is a test
```

```Output
Enter a sentence of four words with scanf: This is a test
This
is
a
test
Enter the same sentence with gets: This is a test
This is a test
```

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
