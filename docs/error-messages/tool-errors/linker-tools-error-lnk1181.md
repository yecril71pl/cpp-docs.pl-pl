---
title: Błąd narzędzi konsolidatora LNK1181
ms.date: 08/22/2018
f1_keywords:
- LNK1181
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
ms.openlocfilehash: d2b28af52a2ca2263a7bad77c8c69242396ff2b4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195256"
---
# <a name="linker-tools-error-lnk1181"></a>Błąd narzędzi konsolidatora LNK1181

nie można otworzyć pliku wejściowego "filename"

Konsolidator nie może odnaleźć `filename`, ponieważ nie istnieje lub nie znaleziono ścieżki.

Niektóre typowe przyczyny wystąpienia błędu LNK1181 obejmują:

- `filename` jest przywoływany jako dodatkowa zależność w linii konsolidatora, ale plik nie istnieje.

- Brak instrukcji **/LIBPATH** , która określa katalog zawierający `filename`.

Aby rozwiązać powyższe problemy, upewnij się, że wszystkie pliki, do których odwołuje się linia konsolidatora, znajdują się w systemie.  Upewnij się również, że istnieje instrukcja **/LIBPATH** dla każdego katalogu zawierającego plik zależny od konsolidatora.

Aby uzyskać więcej informacji, zobacz [Pliki lib jako dane wejściowe konsolidatora](../../build/reference/dot-lib-files-as-linker-input.md).

Kolejną możliwą przyczyną LNK1181 jest to, że długa nazwa pliku z osadzonymi spacjami nie jest ujęta w cudzysłów.  W takim przypadku konsolidator będzie rozpoznawał tylko nazwę pliku do pierwszego miejsca, a następnie przyjmuje rozszerzenie pliku. obj.  Rozwiązaniem tej sytuacji jest ujęcie w cudzysłowie długiej nazwy pliku (ścieżki i nazwy pliku).

Kompilowanie z opcją [/p (preprocess to File)](../../build/reference/p-preprocess-to-a-file.md) może spowodować, że LNK1181, ponieważ ta opcja pomija tworzenie plików. obj.

## <a name="see-also"></a>Zobacz też

[/LIBPATH (Dodatkowa Libpath)](../../build/reference/libpath-additional-libpath.md)
