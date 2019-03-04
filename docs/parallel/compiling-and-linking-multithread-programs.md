---
title: Kompilowanie i łączenie programów wielowątkowych
ms.date: 11/04/2016
helpviewer_keywords:
- compiling multithreaded programs
- multithreading [C++], linking programs
- threading [C++], linking programs
- multithreading [C++], compiled programs
- threading [C++], compiled programs
- compiling source code [C++], multithread programs
- linking [C++], multithread programs
ms.assetid: 27589afc-daf2-4f26-b868-a99de5c9dfec
ms.openlocfilehash: bc56c71c4c3c1367d35dd5995054b1d7371ae9de
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283491"
---
# <a name="compiling-and-linking-multithread-programs"></a>Kompilowanie i łączenie programów wielowątkowych

Bounce.c program została wprowadzona w systemie [przykładowy Program C wielowątkowości](sample-multithread-c-program.md).

Programy są kompilowane wielowątkowe domyślnie.

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-within-the-development-environment"></a>Aby skompilować i połącz program wielowątkowy Bounce.c w środowisku programistycznym

1. Na **pliku** menu, kliknij przycisk **New**, a następnie kliknij przycisk **projektu**.

1. W **typów projektów** okienku kliknij **Win32**.

1. W **szablony** okienku kliknij **Aplikacja konsoli Win32**, a następnie nadaj projektowi nazwę.

1. Dodaj plik zawierający kod źródłowy języka C do projektu.

1. Na **kompilacji** menu, skompiluj projekt, klikając **kompilacji** polecenia.

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-the-command-line"></a>Aby skompilować i łączenie programów wielowątkowych Bounce.c z wiersza polecenia

1. Kompilowanie i łączenie program:

    ```
    CL BOUNCE.C
    ```

## <a name="see-also"></a>Zobacz także

[Wielowątkowość z językiem C i podsystemem Win32](multithreading-with-c-and-win32.md)
