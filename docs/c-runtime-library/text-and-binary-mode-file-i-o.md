---
title: Tekst i trybie binarnym pliku we/wy | Dokumenty Microsoft
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.io
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4be1a3619fcd441dbcca53b0a1c369e30f9fb678
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="text-and-binary-mode-file-io"></a>Operacja We/Wy pliku w trybie binarnym i tekstowym

Operacje We/Wy pliku została wykonana w jednym z dwóch trybów tłumaczenia, *tekst* lub *binarne*, w zależności od trybu, w którym plik jest otwarty. Pliki danych zazwyczaj są przetwarzane w trybie tekstowym. Aby kontrolować tryb tłumaczenia pliku, można:

- Zachowaj bieżące ustawienie domyślne i określ alternatywny tryb tylko po otwarciu wybrane pliki.

- Użyj funkcji [_set_fmode —](../c-runtime-library/reference/set-fmode.md) Aby zmienić domyślny tryb dla nowo otwarte pliki. Użyj [_get_fmode —](../c-runtime-library/reference/get-fmode.md) można znaleźć bieżący tryb domyślny. Ustawieniem domyślnym początkowa jest w trybie tekstowym (**_o_text —**).

- Zmień domyślny tryb tłumaczenia bezpośrednio przez ustawienie zmiennej globalnej [_fmode —](../c-runtime-library/fmode.md) w programie. Funkcja **_set_fmode —** ustawia wartość tej zmiennej, ale też można ustawić bezpośrednio.

Podczas wywoływania funkcji otwieranie plików takich jak [_otwórz](../c-runtime-library/reference/open-wopen.md), [fopen —](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s —](../c-runtime-library/reference/fopen-s-wfopen-s.md), [freopen —](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s —](../c-runtime-library/reference/freopen-s-wfreopen-s.md), [_fsopen —](../c-runtime-library/reference/fsopen-wfsopen.md) lub [_sopen_s —](../c-runtime-library/reference/sopen-s-wsopen-s.md), można zastąpić bieżące domyślne ustawienie **_fmode —** , określając odpowiedni argument funkcji [_set_fmode —](../c-runtime-library/reference/set-fmode.md). **Stdin**, **stdout**, i **stderr** strumieni zawsze otwierane w trybie tekstowym domyślnie; można też zastąpić to ustawienie domyślne przy otwieraniu plików. Użyj [_setmode —](../c-runtime-library/reference/setmode.md) Aby zmienić tryb tłumaczenia przy użyciu deskryptorów plików, po otwarciu pliku.

## <a name="see-also"></a>Zobacz też

[Dane wejściowe i wyjściowe](../c-runtime-library/input-and-output.md)<br/>
 [Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
