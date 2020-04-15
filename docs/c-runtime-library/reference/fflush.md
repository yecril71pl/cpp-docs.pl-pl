---
title: fflush
ms.date: 4/2/2020
api_name:
- fflush
- _o_fflush
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
- fflush
helpviewer_keywords:
- streams, flushing
- flushing
- fflush function
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
ms.openlocfilehash: 401f715e99e6304f0726c8b9c96a71d9582dbc1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347165"
---
# <a name="fflush"></a>fflush

Opróżnia strumień.

## <a name="syntax"></a>Składnia

```C
int fflush(
   FILE *stream
);
```

### <a name="parameters"></a>Parametry

*Strumienia*<br/>
Wskaźnik do struktury **PLIK.**

## <a name="return-value"></a>Wartość zwracana

**fflush** zwraca wartość 0, jeśli bufor został pomyślnie opróżniony. Wartość 0 jest również zwracana w przypadkach, w których określony strumień nie ma buforu lub jest otwarty tylko do odczytu. Zwracana wartość **EOF** wskazuje błąd.

> [!NOTE]
> Jeśli **fflush** zwraca **EOF**, dane mogły zostać utracone z powodu błędu zapisu. Podczas konfigurowania programu obsługi błędów krytycznych najbezpieczniej jest wyłączanie buforowania za pomocą funkcji **setvbuf** lub używanie procedur we/wy niskiego poziomu, takich jak **_open**, **_close**i **_write** zamiast funkcji we/wy strumienia.

## <a name="remarks"></a>Uwagi

Funkcja **fflush** opróżnia *strumień*strumienia . Jeśli strumień został otwarty w trybie zapisu lub został otwarty w trybie aktualizacji, a ostatnią operacją był zapis, zawartość buforu strumienia jest zapisywana w podstawowym pliku lub urządzeniu, a bufor jest odrzucany. Jeśli strumień został otwarty w trybie odczytu lub jeśli strumień nie ma buforu, **wywołanie fflush** nie ma wpływu, a każdy bufor jest zachowywany. Wywołanie **fflush** neguje efekt wcześniejszego wywołania **ungetc** dla strumienia. Strumień pozostaje otwarty po wywołaniu.

Jeśli *strumień* ma **wartość NULL**, zachowanie jest takie samo jak wywołanie **fflush** na każdym otwartym strumieniu. Wszystkie strumienie otwarte w trybie zapisu i wszystkie strumienie otwarte w trybie aktualizacji, gdzie ostatnia operacja była zapisu są opróżniane. Wywołanie nie ma wpływu na inne strumienie.

Bufory są zwykle obsługiwane przez system operacyjny, który określa optymalny czas automatycznego zapisywania danych na dysku: gdy bufor jest zapełniony, gdy strumień jest zamknięty lub gdy program kończy się normalnie bez zamykania strumienia. Funkcja zatwierdzania na dysku biblioteki w czasie wykonywania pozwala upewnić się, że dane krytyczne są zapisywane bezpośrednio na dysku, a nie do buforów systemu operacyjnego. Bez przepisywania istniejącego programu, można włączyć tę funkcję, łącząc pliki obiektów programu z COMMODE.OBJ. W wynikowym pliku wykonywalnym wywołania **_flushall** zapisu zawartości wszystkich buforów na dysku. Commode.OBJ dotyczy tylko **_flushall** i **fflush.**

Aby uzyskać informacje dotyczące sterowania funkcją zatwierdzania na dysku, zobacz [Stream we/wy](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md)i [_fdopen](fdopen-wfdopen.md).

Ta funkcja blokuje wątek wywołujący i dlatego jest bezpieczny dla wątków. Aby uzyskać wersję niezablokującą, zobacz **_fflush_nolock**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fflush**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_fflush.c
// Compile with: cl /W4 crt_fflush.c
// This sample gets a number from the user, then writes it to a file.
// It ensures the write isn't lost on crash by calling fflush.
#include <stdio.h>

int * crash_the_program = 0;

int main(void)
{
    FILE * my_file;
    errno_t err = fopen_s(&my_file, "myfile.txt", "w");
    if (my_file && !err)
    {
        printf("Write a number: ");

        int my_number = 0;
        scanf_s("%d", &my_number);

        fprintf(my_file, "User selected %d\n", my_number);

        // Write data to a file immediately instead of buffering.
        fflush(my_file);

        if (my_number == 5)
        {
            // Without using fflush, no data was written to the file
            // prior to the crash, so the data is lost.
            *crash_the_program = 5;
        }

        // Normally, fflush is not needed as closing the file will write the buffer.
        // Note that files are automatically closed and flushed during normal termination.
        fclose(my_file);
    }
    return 0;
}
```

```Input
5
```

```myfile.txt
User selected 5
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
