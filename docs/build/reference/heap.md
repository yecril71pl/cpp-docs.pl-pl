---
title: /HEAP
description: MSVC konsolidatora lub polecenia EDITBIN/HEAP ustawia łączny rozmiar sterty i opcjonalnie rozmiar dodatkowych bloków sterty.
ms.date: 07/07/2020
f1_keywords:
- /heap
helpviewer_keywords:
- heap allocation, setting heap size
- HEAP editbin option
- -HEAP editbin option
- /HEAP editbin option
ms.assetid: 6ce759b5-75b7-44ff-a5fd-3a83a0ba9a48
ms.openlocfilehash: 7976ae2927ca731c83fa42e87da182fee4df3d7c
ms.sourcegitcommit: e17cc8a478b51739d67304d7d82422967b35f716
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/08/2020
ms.locfileid: "86127828"
---
# `/HEAP`

Ustawia rozmiar sterty w bajtach. Ta opcja ma zastosowanie tylko do plików wykonywalnych.

## <a name="syntax"></a>Składnia

> **`/HEAP:`**_`reserve`_\[**`,`**_`commit`_]

## <a name="remarks"></a>Uwagi

*`reserve`* Argument określa łączną początkową alokację sterty w pamięci wirtualnej. **`/HEAP`** Opcja konsolidatora lub [polecenia EDITBIN](editbin-reference.md) zaokrągla określoną wartość do najbliższej wielokrotności 4 bajtów. Domyślnie rozmiar sterty wynosi 1 MB.

Opcjonalny *`commit`* argument podlega interpretacji przez system operacyjny. W systemie operacyjnym Windows określa początkową ilość pamięci fizycznej do przydzielenia. Określa również ilość pamięci do przydzielenia, gdy sterta jest rozwinięta. Przydzielona pamięć wirtualna powoduje, że miejsce jest zarezerwowane w pliku stronicowania. Wyższa *`commit`* wartość umożliwia systemowi przydzielanie pamięci rzadziej, gdy aplikacja wymaga większej liczby miejsc sterty, ale zwiększa wymagania dotyczące pamięci i prawdopodobnie czas uruchomienia aplikacji. *`commit`* Wartość musi być mniejsza lub równa *`reserve`* wartości. Wartość domyślna to 4 KB.

Określ *`reserve`* wartości i *`commit`* w notacji dziesiętnej, szesnastkowej języka C lub ósemkowej. Na przykład wartość 1 MB może być określona jako 1048576 w postaci dziesiętnej lub jako 0x100000 w formacie szesnastkowym lub jako 04000000 w postaci ósemkowej. Wartości domyślne są równoważne opcji **`/HEAP:1048576,4096`** .

### <a name="example"></a>Przykład

To przykładowe polecenie linku tworzy *main.exe* pliku wykonywalnego, który ma rezerwę sterty wynoszącą 2 MB. Sterta wstępna i późniejsze rozszerzenia sterty są dostępne w blokach 64 KB:

**`link /heap:0x200000,0x10000 main.obj`**

### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać więcej informacji, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz pozycję **Właściwości konfiguracji**  >  **Linker**  >  Strona właściwości**systemu** konsolidatora.

1. Ustaw właściwości **rozmiar rezerwacji sterty** i **rozmiar zatwierdzenia sterty** , a następnie wybierz przycisk **OK** lub **Zastosuj** , aby zapisać zmiany.

## <a name="see-also"></a>Zobacz też

[Opcje polecenia EDITBIN](editbin-options.md)\
[Opcje konsolidatora MSVC](linker-options.md)
