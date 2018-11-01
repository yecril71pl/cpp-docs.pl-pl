---
title: Operacja We/Wy pliku w trybie binarnym i tekstowym
ms.date: 04/11/2018
f1_keywords:
- c.io
helpviewer_keywords:
- files [C++], open functions
- I/O [CRT], text files
- functions [CRT], file access
- binary access, binary mode file I/O
- translation, modes
- I/O [CRT], binary
- text files, I/O
- I/O [CRT], translation modes
- translation modes (file I/O)
- binary access
ms.assetid: 3196e321-8b87-4609-b302-cd6f3c516051
ms.openlocfilehash: 54b095913ea4ec25fe5bd077d38a6bba303a7b72
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546292"
---
# <a name="text-and-binary-mode-file-io"></a>Operacja We/Wy pliku w trybie binarnym i tekstowym

Operacje We/Wy pliku została wykonana w jednym z dwóch trybów tłumaczenia *tekstu* lub *binarne*, w zależności od trybu, w którym plik jest otwarty. Pliki danych zwykle są przetwarzane w trybie tekstowym. Aby kontrolować tryb tłumaczenia pliku, jeden wykonywać następujące czynności:

- Zachowaj bieżące ustawienie domyślne i określić alternatywne tryb tylko wtedy, gdy otworzysz wybrane pliki.

- Użyj funkcji [_set_fmode —](../c-runtime-library/reference/set-fmode.md) zmienić domyślny tryb dla nowo otwarte pliki. Użyj [_get_fmode —](../c-runtime-library/reference/get-fmode.md) można znaleźć bieżący tryb domyślny. Początkowa domyślnym ustawieniem jest tryb tekstu (**_O_TEXT**).

- Zmień domyślny tryb translacji bezpośrednio przez ustawienie zmiennej globalnej [_fmode](../c-runtime-library/fmode.md) w programach. Funkcja **_set_fmode —** ustawia wartość tej zmiennej, ale również można ustawić bezpośrednio.

Jeśli wywołasz funkcję otwartego pliku takich jak [_otwórz](../c-runtime-library/reference/open-wopen.md), [fopen —](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s —](../c-runtime-library/reference/fopen-s-wfopen-s.md), [freopen —](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s —](../c-runtime-library/reference/freopen-s-wfreopen-s.md), [_fsopen —](../c-runtime-library/reference/fsopen-wfsopen.md) lub [_sopen_s —](../c-runtime-library/reference/sopen-s-wsopen-s.md), można zastąpić bieżące domyślne ustawienie **_fmode** , określając odpowiedni argument funkcji [_set_fmode —](../c-runtime-library/reference/set-fmode.md). **Stdin**, **stdout**, i **stderr** strumieni zawsze domyślnie otwierane w trybie tekstowym; możesz również zastąpić to ustawienie domyślne podczas otwierania plików. Użyj [_setmode —](../c-runtime-library/reference/setmode.md) Aby zmienić tryb translacji przy użyciu deskryptora pliku, po otwarciu pliku.

## <a name="see-also"></a>Zobacz też

[Dane wejściowe i wyjściowe](../c-runtime-library/input-and-output.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
