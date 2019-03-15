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
ms.openlocfilehash: 48ad9423ae35c22a97a873fe6a2a0479c12ab33b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817793"
---
# <a name="link-input-files"></a>Pliki wyjściowe LINK

Konsolidator udostępniać pliki, które zawierają obiekty, importu i standardowych bibliotek, zasobów, definicje modułów i polecenia dane wejściowe. ŁĄCZE nie używa rozszerzeń plików umożliwiają założeń dotyczących zawartości pliku. Zamiast tego łącza sprawdza, czy każdy plik wejściowy, aby ustalić, jakiego typu pliku jest.

Pliki obiektów w wierszu polecenia są przetwarzane w kolejności, w jakiej znajdują się w wierszu polecenia. Biblioteki są przeszukiwane w kolejności wiersza polecenia, za pomocą następujące ostrzeżenie: Liczba nierozpoznanych symboli, które są po łączy w pliku obiektu z biblioteki są wyszukiwane w tej bibliotece najpierw, a następnie polecenie następujące biblioteki z poziomu wiersza polecenia i [/DEFAULTLIB (Określanie domyślnej biblioteki)](defaultlib-specify-default-library.md) dyrektywy, a następnie do żadnych bibliotek na początku wiersza polecenia.

> [!NOTE]
>  LINK nie będzie akceptował średnikiem (lub jakikolwiek inny znak) jako początek komentarza w plikach odpowiedzi i kolejność plików. Średnikami są rozpoznawane tylko jako początek komentarze w plikach definicji modułu (.def).

ŁĄCZE używa następujących typów plików wejściowych:

- [pliki .obj](dot-obj-files-as-linker-input.md)

- [pliki .netmodule](netmodule-files-as-linker-input.md)

- [pliki .lib](dot-lib-files-as-linker-input.md)

- [.EXP — pliki](dot-exp-files-as-linker-input.md)

- [.def — pliki](dot-def-files-as-linker-input.md)

- [pliki .pdb](dot-pdb-files-as-linker-input.md)

- [pliki .res](dot-res-files-as-linker-input.md)

- [pliki .exe](dot-exe-files-as-linker-input.md)

- [pliki txt](dot-txt-files-as-linker-input.md)

- [.ilk — pliki](dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
