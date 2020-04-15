---
title: Pliki wyjściowe LINK
ms.date: 11/04/2016
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
ms.openlocfilehash: aec71d4622821618f377953d36a9676e2233eefc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328204"
---
# <a name="link-input-files"></a>Pliki wyjściowe LINK

Należy udostępnić konsolidatorowi pliki zawierające obiekty, biblioteki importowe i standardowe, zasoby, definicje modułów i dane wejściowe poleceń. LINK nie używa rozszerzeń plików do wprowadzania założeń dotyczących zawartości pliku. Zamiast tego LINK sprawdza każdy plik wejściowy, aby określić, jaki to jest rodzaj pliku.

Pliki obiektów w wierszu polecenia są przetwarzane w kolejności, w jakiej pojawiają się w wierszu polecenia. Biblioteki są również przeszukiwane w kolejności wiersza polecenia, z następującym zastrzeżeniem: Symbole, które nie zostały rozpoznane podczas wprowadzania pliku obiektu z biblioteki, są najpierw wyszukiwane w tej bibliotece, a następnie następujące biblioteki z wiersza polecenia i [/DEFAULTLIB (Określ bibliotekę domyślną),](defaultlib-specify-default-library.md) a następnie do wszystkich bibliotek na początku wiersza polecenia.

> [!NOTE]
> LINK nie akceptuje już średnika (lub innego znaku) jako początek komentarza w plikach odpowiedzi i plikach zamówień. Średniki są rozpoznawane tylko jako początek komentarzy w plikach definicji modułu (.def).

LINK używa następujących typów plików wejściowych:

- [Pliki obj](dot-obj-files-as-linker-input.md)

- [pliki .netmodule](netmodule-files-as-linker-input.md)

- [.lib](dot-lib-files-as-linker-input.md)

- [pliki exp](dot-exp-files-as-linker-input.md)

- [pliki def](dot-def-files-as-linker-input.md)

- [pliki pdb](dot-pdb-files-as-linker-input.md)

- [pliki .res](dot-res-files-as-linker-input.md)

- [pliki exe](dot-exe-files-as-linker-input.md)

- [pliki txt](dot-txt-files-as-linker-input.md)

- [pliki .ilk](dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>Zobacz też

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
