---
title: Pliki wyjściowe LINK
ms.date: 11/04/2016
f1_keywords:
- link
helpviewer_keywords:
- files [C++], LINK
- module definition files
- resources [C++], linker files
- LINK tool [C++], input files
- module definition files, linker files
- input files [C++], LINK
- linker [C++], input files
- import libraries [C++], linker files
- command input to linker files [C++]
ms.assetid: bb26fcc5-509a-4620-bc3e-b6c6e603a412
ms.openlocfilehash: a5aaf162a16b6989ac1abbcb6a574af1c31b543a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550556"
---
# <a name="link-input-files"></a>Pliki wyjściowe LINK

Konsolidator udostępniać pliki, które zawierają obiekty, importu i standardowych bibliotek, zasobów, definicje modułów i polecenia dane wejściowe. ŁĄCZE nie używa rozszerzeń plików umożliwiają założeń dotyczących zawartości pliku. Zamiast tego łącza sprawdza, czy każdy plik wejściowy, aby ustalić, jakiego typu pliku jest.

Pliki obiektów w wierszu polecenia są przetwarzane w kolejności, w jakiej znajdują się w wierszu polecenia. Biblioteki są przeszukiwane w kolejności wiersza polecenia, za pomocą następujące ostrzeżenie: symboli, które są nierozwiązane, kiedy łączy w pliku obiektu z biblioteki są wyszukiwane w tej bibliotece najpierw, a następnie polecenie następujące biblioteki z wiersza polecenia i [/DEFAULTLIB (Określanie domyślnej biblioteki)](../../build/reference/defaultlib-specify-default-library.md) dyrektywy, a następnie do żadnych bibliotek na początku wiersza polecenia.

> [!NOTE]
>  LINK nie będzie akceptował średnikiem (lub jakikolwiek inny znak) jako początek komentarza w plikach odpowiedzi i kolejność plików. Średnikami są rozpoznawane tylko jako początek komentarze w plikach definicji modułu (.def).

ŁĄCZE używa następujących typów plików wejściowych:

- [pliki .obj](../../build/reference/dot-obj-files-as-linker-input.md)

- [pliki .netmodule](../../build/reference/netmodule-files-as-linker-input.md)

- [pliki .lib](../../build/reference/dot-lib-files-as-linker-input.md)

- [.EXP — pliki](../../build/reference/dot-exp-files-as-linker-input.md)

- [.def — pliki](../../build/reference/dot-def-files-as-linker-input.md)

- [pliki .pdb](../../build/reference/dot-pdb-files-as-linker-input.md)

- [pliki .res](../../build/reference/dot-res-files-as-linker-input.md)

- [pliki .exe](../../build/reference/dot-exe-files-as-linker-input.md)

- [pliki txt](../../build/reference/dot-txt-files-as-linker-input.md)

- [.ilk — pliki](../../build/reference/dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)