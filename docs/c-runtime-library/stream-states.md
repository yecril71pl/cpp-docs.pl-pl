---
title: Stany strumieni
ms.date: 11/04/2016
helpviewer_keywords:
- streams, states
ms.assetid: 5f28c968-f132-403f-968c-8417ff315e52
ms.openlocfilehash: d51f24b82c10d58e91f5d20b6656eb16621004ac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481175"
---
# <a name="stream-states"></a>Stany strumieni

Na poniższej ilustracji przedstawiono prawidłowe stany i przejścia stanu, dla strumienia.

![Stream](../c-runtime-library/media/stream.gif "strumienia")

Każdy z okręgów oznacza stanu stabilnego. Każdy z wierszy oznacza przejścia, które mogą wystąpić w wyniku wywołania funkcji, która przetwarza strumień. Pięć grup funkcji może spowodować stanami.

Funkcje w pierwszych trzech grup są deklarowane w \<stdio.h >:

- Bajt odczytu funkcje — [fgetc —](../c-runtime-library/reference/fgetc-fgetwc.md), [fgets](../c-runtime-library/reference/fgets-fgetws.md), [fread —](../c-runtime-library/reference/fread.md), [fscanf —](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [getc —](../c-runtime-library/reference/getc-getwc.md), [ getchar](../c-runtime-library/reference/getc-getwc.md), [pobiera](../c-runtime-library/gets-getws.md), [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md), i [ungetc —](../c-runtime-library/reference/ungetc-ungetwc.md)

- Bajt pisać funkcje — [fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fputc](../c-runtime-library/reference/fputc-fputwc.md), [fputs —](../c-runtime-library/reference/fputs-fputws.md), [fwrite —](../c-runtime-library/reference/fwrite.md), [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md), [putc](../c-runtime-library/reference/putc-putwc.md), [putchar](../c-runtime-library/reference/putc-putwc.md), [umieszcza](../c-runtime-library/reference/puts-putws.md), [vfprintf —](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), i [vprintf —](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)

- Funkcje położenia — [fflush —](../c-runtime-library/reference/fflush.md), [fseek](../c-runtime-library/reference/fseek-fseeki64.md), [fsetpos](../c-runtime-library/reference/fsetpos.md), i [przewinąć do tyłu](../c-runtime-library/reference/rewind.md)

Funkcje w pozostałych dwóch grup są deklarowane w \<wchar.h >:

- Całej odczytu funkcje — [fgetwc —](../c-runtime-library/reference/fgetc-fgetwc.md), [fgetws —](../c-runtime-library/reference/fgets-fgetws.md), [fwscanf —](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [getwc —](../c-runtime-library/reference/getc-getwc.md), [getwchar —](../c-runtime-library/reference/getc-getwc.md), [ungetwc —](../c-runtime-library/reference/ungetc-ungetwc.md), i [wscanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md),

- Całej pisać funkcje — [fwprintf —](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fputwc —](../c-runtime-library/reference/fputc-fputwc.md), [fputws —](../c-runtime-library/reference/fputs-fputws.md), [putwc](../c-runtime-library/reference/putc-putwc.md), [putwchar](../c-runtime-library/reference/fputc-fputwc.md), [vfwprintf —](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), [vwprintf —](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md), i [wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md),

Diagram stanu pokazuje, że należy wywołać jedną z pozycji funkcji między większość zapisu i operacji odczytu:

- Nie można wywołać funkcji odczytu, jeśli ostatniej operacji na strumieniu zapisu.

- Nie można wywołać funkcję zapisu jeśli ostatnią operację na strumień odczytu, chyba że, odczytać operacji Ustaw wskaźnik końca pliku.

Na koniec diagram stanu pokazuje, że operacja pozycji nigdy nie zmniejsza liczbę wywołań prawidłową funkcją, które można wykonać.

## <a name="see-also"></a>Zobacz też

[Pliki i strumienie](../c-runtime-library/files-and-streams.md)