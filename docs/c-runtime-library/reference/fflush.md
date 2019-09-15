---
title: fflush
ms.date: 09/11/2019
api_name:
- fflush
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
ms.openlocfilehash: 966ff5622faaccd2d9e501b39da99b010e841c22
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940943"
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

*stream*<br/>
Wskaźnik do struktury **pliku** .

## <a name="return-value"></a>Wartość zwracana

**fflush** zwraca wartość 0, jeśli bufor został pomyślnie opróżniony. Wartość 0 jest również zwracana w przypadkach, w których określony strumień nie ma buforu lub jest otwarty tylko do odczytu. Wartość zwracana przez **znacznik EOF** wskazuje na błąd.

> [!NOTE]
> Jeśli **fflush** zwraca **znacznik EOF**, dane mogły zostać utracone z powodu błędu zapisu. Podczas konfigurowania programu obsługi błędów krytycznych najbezpieczniejszym sposobem jest wyłączenie buforowania przy użyciu funkcji **setvbuf —** lub użycie procedur we/wy niskiego poziomu, takich jak **_open**, **_close**i **_write** zamiast funkcji we/wy strumienia.

## <a name="remarks"></a>Uwagi

Funkcja **fflush** opróżnia *strumień*strumienia. Jeśli strumień został otwarty w trybie zapisu lub został otwarty w trybie aktualizacji, a Ostatnia operacja była zapisu, zawartość buforu strumienia jest zapisywana w źródłowym pliku lub urządzeniu i bufor jest odrzucany. Jeśli strumień został otwarty w trybie odczytu lub strumień nie ma buforu, wywołanie do **fflush** nie ma żadnego efektu i wszystkie bufory są zachowywane. Wywołanie **fflush** powoduje negację efektu dowolnego wcześniejszego wywołania **ungetc —** strumienia. Strumień pozostaje otwarty po wywołaniu.

Jeśli *strumień* ma **wartość null**, zachowanie jest takie samo jak wywołanie **fflush** w każdym otwartym strumieniu. Wszystkie strumienie otwarte w trybie zapisu i wszystkie strumienie otwarte w trybie aktualizacji, w których Ostatnia operacja była zapisu, są opróżniane. Wywołanie nie ma wpływu na inne strumienie.

Bufory są zwykle obsługiwane przez system operacyjny, który określa optymalny czas zapisywania danych na dysku: gdy bufor jest zapełniony, gdy strumień jest zamknięty lub gdy program kończy normalne działanie bez zamykania strumienia. Funkcja zatwierdzania na dysku w bibliotece wykonawczej pozwala zagwarantować, że krytyczne dane są zapisywane bezpośrednio na dysku, a nie w buforach systemu operacyjnego. Bez ponownego zapisywania istniejącego programu można włączyć tę funkcję, łącząc pliki obiektów programu z TOWARami. OBJ. W utworzonym pliku wykonywalnym wywołania **_flushall** zapisują zawartość wszystkich buforów na dysku. Tylko **_flushall** i **fflush** mają wpływ na towary. obj.

Aby uzyskać informacje dotyczące kontrolowania funkcji zatwierdzania na dysku, zobacz [przesyłanie strumieniowe we/wy](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md)i [_fdopen](fdopen-wfdopen.md).

Ta funkcja blokuje wątek wywołujący i dlatego jest bezpieczna wątkowo. W przypadku wersji, która nie jest blokowana, zobacz **_fflush_nolock**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**fflush**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
