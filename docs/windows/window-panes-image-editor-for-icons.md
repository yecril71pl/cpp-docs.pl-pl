---
title: Okienka (Edytor obrazów dla ikon)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- graphics editor [C++]
- Image editor [C++], panes
- Image editor [C++], magnification
- grids, pixel
- pixel grid, Image editor
- Image editor [C++], pixel grid
- Image editor [C++], grid settings
- grid settings, Image editor
ms.assetid: d66ea5b3-e2e2-4fc4-aa99-f50022cc690e
ms.openlocfilehash: 72b7cf056147cdbd216d861f0e710da423951c5a
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560312"
---
# <a name="window-panes-image-editor-for-icons"></a>Okienka (Edytor obrazów dla ikon)

**Edytora obrazów** okna zwykle wyświetla obraz na dwa okienka rozdzielone pasek podziału. Jeden widok jest rzeczywisty rozmiar, a druga powiększenia (domyślny współczynnik rozszerzenia jest 6). Widoki te dwa okienka są automatycznie aktualizowane: zmiany wprowadzone w jednym okienku natychmiast są wyświetlane w innym. Dwa okienka ułatwiają pracować nad powiększania widoku obrazu, w którym można odróżnić poszczególnych pikseli i, w tym samym czasie obserwować wpływ swoją pracę na widoku rzeczywisty rozmiar obrazu.

Tyle miejsca, ile potrzeba korzysta z okienka po lewej stronie (do połowy **obraz** okna) do wyświetlenia widoku powiększeniem 1:1 (opcja domyślna) obrazu. W okienku po prawej stronie wyświetla powiększonego (6:1 powiększenie domyślnie). Możesz zmienić powiększenia w każdym za pomocą okienka **Magnify** narzędzie [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md) lub za pomocą klawiszy skrótów.

Można powiększyć mniejszych okienku **edytora obrazów** okno i użyj dwa okienka, aby pokazać różnych regionach duży obraz. Wybierz w okienku, aby ją wybrać.

Względne rozmiary okienek można zmienić, ustawiając kursor na pasek podziału i przenoszenie pasek podziału w prawo lub lewo. Pasek podziału można przenieść do dowolnej stronie, aby pracować nad tylko jedno okienko.

Jeśli **edytora obrazów** okienko jest powiększony o 4 lub nowszej, może wyświetlić siatkę pikseli, ograniczającego piksele na obrazie.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-change-the-magnification-factor"></a>Aby zmienić stopień powiększenia

Domyślnie **obraz** wyświetlania widoku w okienku po lewej stronie w rzeczywistym rozmiarze w edytorze i widok, w okienku po prawej stronie 6 razy rzeczywisty rozmiar. Współczynnika powiększenia (widoczny na pasku stanu w dolnej części obszaru roboczego) jest stosunek między rzeczywisty rozmiar obrazu i wyświetlany rozmiar. Domyślny współczynnik wynosi 6 i zakres jest z zakresu od 1 do 10.

1. Wybierz **edytora obrazów** okienko współczynnika powiększenia, którego chcesz zmienić.

1. Na [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md), wybierz strzałkę po prawej stronie [narzędzie Powiększenie](../windows/toolbar-image-editor-for-icons.md) i wybierz współczynnika powiększenia z podmenu: **1 X**, **2 X**, **6 X**, lub **8 X**.

   > [!NOTE]
   > Aby wybrać współczynnika powiększenia, inne niż te wymienione w **Magnify** narzędzie, korzystanie z klawiszy skrótów.

## <a name="to-display-or-hide-the-pixel-grid"></a>Aby wyświetlić lub ukryć siatkę pikseli

Dla wszystkich **edytora obrazów** okienka przy użyciu współczynnika powiększenia 4 lub większą, można wyświetlić siatkę ograniczającego piksele na obrazie.

1. Na **obraz** menu, wybierz opcję **ustawienia siatki**.

1. Wybierz **siatkę pikseli** pole wyboru, aby wyświetlić siatkę, lub wyczyść pole, aby ukryć siatkę.

> [!TIP]
> Etykietki narzędzi są wyświetlane po umieszczeniu kursora na przycisku paska narzędzi. Poniższe wskazówki mogą pomóc w identyfikacji funkcji każdego przycisku.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)