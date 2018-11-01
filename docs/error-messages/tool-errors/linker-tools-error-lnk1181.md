---
title: Błąd narzędzi konsolidatora LNK1181
ms.date: 08/22/2018
f1_keywords:
- LNK1181
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
ms.openlocfilehash: 834220e6325e332a07c3865b5ff66e1bbc1b8c69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657992"
---
# <a name="linker-tools-error-lnk1181"></a>Błąd narzędzi konsolidatora LNK1181

Nie można otworzyć pliku wejściowego 'NazwaPliku'

Konsolidator nie może odnaleźć `filename` ponieważ nie istnieje lub nie można odnaleźć ścieżki.

Niektóre typowe przyczyny błędu LNK1181 obejmują:

- `filename` jest przywoływany jako dodatkową zależność w linii konsolidatora, ale plik nie istnieje.

- A **/libpath —** instrukcję, która określa katalogu zawierającego `filename` są spełnione.

Aby rozwiązać problemy powyżej, upewnij się, że wszystkie pliki, do których odwołuje się w linii konsolidatora są obecne w systemie.  Upewnij się również ma **/libpath —** instrukcji dla każdego katalogu zawierającego plik konsolidatora-zależnych od ustawień lokalnych.

Aby uzyskać więcej informacji, zobacz [pliki .lib — wejście konsolidatora](../../build/reference/dot-lib-files-as-linker-input.md).

Inną możliwą przyczyną LNK1181 to, że długiej nazwy pliku ze spacjami nie zostało ujęte w znaki cudzysłowu.  W takiej sytuacji konsolidator będzie rozpoznają nazwę pliku do pierwszą przestrzeń, a następnie przyjęto założenie, rozszerzenie pliku. obiektu  Rozwiązaniem tej sytuacji jest ująć długiej nazwy pliku (ścieżka, a także plik name) w znaki cudzysłowu.

Kompilowanie przy użyciu [/P (Przetwarzaj wstępnie do pliku)](../../build/reference/p-preprocess-to-a-file.md) opcji może spowodować LNK1181, ponieważ ta opcja pomija tworzenie plików .obj.

## <a name="see-also"></a>Zobacz też

[/LIBPATH (Dodatkowa Libpath)](../../build/reference/libpath-additional-libpath.md)