---
title: Stany strumieni | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- streams, states
ms.assetid: 5f28c968-f132-403f-968c-8417ff315e52
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 418ed7c98523bf8944afcccc13a0e9020036940f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32413139"
---
# <a name="stream-states"></a>Stany strumieni
Na poniższej ilustracji przedstawiono prawidłowe stany i przejść stanu dla strumienia.  
  
 ![Strumień](../c-runtime-library/media/stream.gif "strumienia")  
  
 Każdy z kółka oznacza stabilności. Każdy z wierszy oznacza przejście, które mogą wystąpić w wyniku wywołania funkcji, która działa w strumieniu. Pięć grup funkcji może spowodować przejścia stanu.  
  
 Funkcje w pierwszych trzech grup są zadeklarowane w \<stdio.h >:  
  
-   Bajt odczytać funkcji — [fgetc —](../c-runtime-library/reference/fgetc-fgetwc.md), [fgets —](../c-runtime-library/reference/fgets-fgetws.md), [fread —](../c-runtime-library/reference/fread.md), [fscanf —](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [getc —](../c-runtime-library/reference/getc-getwc.md), [ getchar](../c-runtime-library/reference/getc-getwc.md), [pobiera](../c-runtime-library/gets-getws.md), [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md), i [ungetc —](../c-runtime-library/reference/ungetc-ungetwc.md)  
  
-   Bajt pisanie funkcji — [fprintf —](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fputc —](../c-runtime-library/reference/fputc-fputwc.md), [fputs —](../c-runtime-library/reference/fputs-fputws.md), [fwrite —](../c-runtime-library/reference/fwrite.md), [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md), [putc —](../c-runtime-library/reference/putc-putwc.md), [putchar —](../c-runtime-library/reference/putc-putwc.md), [umieszcza](../c-runtime-library/reference/puts-putws.md), [vfprintf —](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), i [vprintf —](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)  
  
-   Funkcje pozycji — [fflush —](../c-runtime-library/reference/fflush.md), [fseek](../c-runtime-library/reference/fseek-fseeki64.md), [fsetpos —](../c-runtime-library/reference/fsetpos.md), i [przewijanie do tyłu](../c-runtime-library/reference/rewind.md)  
  
 Funkcje w pozostałych dwóch grupach są zadeklarowane w \<wchar.h >:  
  
-   Całej odczytać funkcji — [fgetwc —](../c-runtime-library/reference/fgetc-fgetwc.md), [fgetws —](../c-runtime-library/reference/fgets-fgetws.md), [fwscanf —](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md), [getwc —](../c-runtime-library/reference/getc-getwc.md), [getwchar —](../c-runtime-library/reference/getc-getwc.md), [ungetwc —](../c-runtime-library/reference/ungetc-ungetwc.md), i [wscanf —](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md),  
  
-   Pisanie całej funkcji — [fwprintf —](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fputwc —](../c-runtime-library/reference/fputc-fputwc.md), [fputws —](../c-runtime-library/reference/fputs-fputws.md), [putwc —](../c-runtime-library/reference/putc-putwc.md), [putwchar —](../c-runtime-library/reference/fputc-fputwc.md), [vfwprintf —](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md), [vwprintf —](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md), i [wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md),  
  
 Diagram stanu pokazuje, że należy wywołać jednej z funkcji pozycji między większość operacji odczytu i zapisu:  
  
-   Nie można wywołać funkcji odczytu, jeśli ostatniej operacji na strumieniu zapisu.  
  
-   Nie można wywołać funkcji zapisu Jeśli ostatniej operacji na strumieniu odczytu, chyba że który odczytywać zestawu operacji wskaźnika końca pliku.  
  
 Na koniec diagram stanu pokazuje, czy operacja pozycji nigdy nie zmniejsza liczbę wywołań funkcji prawidłowe, które można wykonać.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki i strumienie](../c-runtime-library/files-and-streams.md)