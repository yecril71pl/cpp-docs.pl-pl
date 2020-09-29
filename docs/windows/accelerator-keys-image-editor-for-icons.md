---
title: Klawisze skrótów (Edytor obrazów C++ dla ikon)
ms.date: 02/15/2019
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
ms.openlocfilehash: 02ac25b693e4d8f7bb6739708d23eb1df0ebf190
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500872"
---
# <a name="accelerator-keys-c-image-editor-for-icons"></a>Klawisze skrótów (Edytor obrazów C++ dla ikon)

Poniżej znajdują się klawisze skrótów dla poleceń edytora obrazów, które są domyślnie powiązane z kluczami. Aby zmienić klawisze skrótów, przejdź do menu **Tools**  >  **Opcje** narzędzia i wybierz polecenie **Klawiatura** w folderze **środowisko** . Aby uzyskać więcej informacji, zobacz [Identyfikowanie i Dostosowywanie skrótów klawiaturowych](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

> [!NOTE]
> Opcje dostępne w oknach dialogowych oraz nazwy i lokalizacje poleceń menu, które są widoczne, mogą się różnić od tego, co opisano w pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, przejdź do menu **Narzędzia**  >  **Opcje importowania i eksportowania ustawień**. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

|Polecenie|Klucze|Opis|
|-------------|----------|-----------------|
|Image. AirBrushTool|**Ctrl**  +  **A**|Rysuje przy użyciu aerografu z wybranym rozmiarem i kolorem.|
|Image.BrushTool|**Ctrl**  +  **B**|Rysuje przy użyciu pędzla o wybranym kształcie, rozmiarze i kolorze.|
|Image. CopyAndOutlineSelection|**Ctrl**  +  **SHIFT**  +  **U**|Tworzy kopię bieżącego zaznaczenia i zawiera jej obramowanie. Jeśli kolor tła jest zawarty w bieżącym zaznaczeniu, zostanie on wykluczony, jeśli wybrano opcję [przezroczysty](./image-editor-for-icons.md) .|
|Image.DrawOpaque|**Ctrl**  +  **J**|Sprawia, że bieżące zaznaczenie jest [nieprzezroczyste lub przezroczyste](./image-editor-for-icons.md).|
|Image.EllipseTool|**Ctrl**  +  **P**|Rysuje elipsę o wybranej szerokości linii i kolorze.|
|Image. EraserTool|**Ctrl**  +  **SHIFT**  +  **I**|Wymazuje część obrazu (z bieżącym kolorem tła).|
|Image.FilledEllipseTool|**Ctrl**  +  **SHIFT**  +  **Alt**  +  **P**|Rysuje wypełnioną elipsę.|
|Image.FilledRectangleTool|**Ctrl**  +  **SHIFT**  +  **Alt**  +  **R**|Rysuje wypełniony prostokąt.|
|Image. FilledRoundRectangleTool|**Ctrl**  +  **SHIFT**  +  **Alt**  +  **W**|Rysuje wypełniony prostokąt zaokrąglony.|
|Image.FillTool|**Ctrl**  +  **F**|Wypełnia obszar.|
|Image.FlipHorizontal|**Ctrl**  +  **H**|Przerzuca obraz lub zaznaczenie w poziomie.|
|Image.FlipVertical|**SHIFT** +  **Alt**  +  **H**|Przerzuca obraz lub zaznaczenie w pionie.|
|Image.LargerBrush|**Przytrzymaj** + **=**|Zwiększa rozmiar pędzla o jeden piksel w każdym kierunku. Aby zmniejszyć rozmiar pędzla, zobacz Image. SmallerBrush w tej tabeli.|
|Image.LineTool|**Ctrl**  +  **L**|Rysuje linię prostą o wybranym kształcie, rozmiarze i kolorze.|
|Image.MagnificationTool|**Ctrl**  +  **M**|Aktywuje narzędzie **Powiększ** , które umożliwia powiększanie określonych sekcji obrazu.|
|Image.Magnify|**Ctrl**  +  **SHIFT**  +  **M**|Przełącza między bieżącym powiększeniem i powiększeniem 1:1.|
|Image.NewImageType|**Insert**|Uruchamia okno [ \<Device> dialogowe Nowy typ obrazu](./creating-an-icon-or-other-image-image-editor-for-icons.md) , za pomocą którego można utworzyć obraz dla innego typu obrazu.|
|Image.NextColor|**Ctrl**  +  **]**<br /><br /> — lub —<br /><br /> **Ctrl**  +  **Strzałka w prawo**|Zmienia kolor pierwszego planu rysunku na następny kolor palety.|
|Image.NextRightColor|**Ctrl**  +  **SHIFT**  +  **]**<br /><br /> — lub —<br /><br /> **SHIFT**  +  **Ctrl**  +  **Strzałka w prawo**|Zmienia kolor tła rysunku na następny kolor palety.|
|Image.OutlinedEllipseTool|**SHIFT**  +  **Alt**  +  **P**|Rysuje wypełnioną elipsę z konturem.|
|Image.OutlinedRectangleTool|**SHIFT**  +  **Alt**  +  **R**|Rysuje wypełniony prostokąt z konturem|
|Image. OutlinedRoundRectangleTool|**SHIFT**  +  **Alt**  +  **W**|Rysuje wypełniony okrągły prostokąt z konturem.|
|Image.PencilTool|**Ctrl**  +  **I**|Rysuje przy użyciu jednopikselowego ołówka.|
|Image.PreviousColor|**Ctrl**  +  **[**<br /><br /> — lub —<br /><br /> **Ctrl**  +  **Strzałka w lewo**|Zmienia kolor pierwszego planu rysunku na poprzedni kolor z palety.|
|Image.PreviousRightColor|**Ctrl**  +  **SHIFT**  +  **[**<br /><br /> — lub —<br /><br /> **SHIFT**  +  **Ctrl**  +  **Strzałka w lewo**|Zmienia kolor tła rysunku na poprzedni kolor palety.|
|Image.RectangleSelectionTool|**SHIFT**  +  **Alt**  +  **S**|Zaznacza prostokątną część obrazu do przeniesienia, skopiowania lub edycji.|
|Image.RectangleTool|ATL + R|Rysuje prostokąt o wybranej szerokości linii i kolorze.|
|Image.Rotate90Degrees|**Ctrl**  +  **SHIFT**  +  **H**|Obraca obraz lub zaznaczenie o 90 stopni.|
|Image.RoundedRectangleTool|**Alt**  +  **W**|Rysuje prostokąt zaokrąglony o wybranej szerokości linii i kolorze.|
|Image.ShowGrid|**Ctrl**  +  **Alt**  +  **S**|Włącza/wyłącza siatkę pikseli (zaznacza lub czyści opcję **Siatka pikseli** w [oknie dialogowym Ustawienia siatki](./image-editor-for-icons.md)).|
|Image.ShowTileGrid|**Ctrl**  +  **SHIFT**  +  **Alt**  +  **S**|Włącza/wyłącza siatkę kafelków (zaznacza lub czyści opcję **siatki kafelków** w [oknie dialogowym Ustawienia siatki](./image-editor-for-icons.md)).|
|Image.SmallBrush|**Ctrl**  +  **.** (kropka)|Zmniejsza rozmiar **pędzla** do jednego piksela. (Zobacz również Image. LargerBrush i Image. SmallerBrush w tej tabeli).|
|Image.SmallerBrush|**Ctrl**  +  Ctrl **-** przed|Zmniejsza rozmiar pędzla o jeden piksel w każdym kierunku. Aby ponownie rozwinąć rozmiar pędzla, zobacz Image. LargerBrush w tej tabeli.|
|Image.TextTool|**Ctrl**  +  **T**|Otwiera [okno dialogowe Narzędzie tekstowe](./image-editor-for-icons.md).|
|Image. UseSelectionAsBrush|**Ctrl**  +  **U**|Rysuje przy użyciu bieżącego zaznaczenia jako pędzla.|
|Image.ZoomIn|**Ctrl**  +  **SHIFT**  +  **.** (kropka)<br /><br /> — lub —<br /><br /> **Ctrl**  +  **Strzałka w górę**|Zwiększa powiększenie bieżącego widoku.|
|Image.ZoomOut|**Ctrl**  +  **,** (przecinek)<br /><br /> — lub —<br /><br /> **Ctrl**  +  **Strzałka w dół**|Zmniejsza powiększenie bieżącego widoku.|

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Edytor obrazów dla ikon](image-editor-for-icons.md)<br/>
[Instrukcje: Tworzenie ikony lub innego obrazu](creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Instrukcje: Edytowanie obrazu](selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Instrukcje: korzystanie z narzędzia do rysowania](using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Instrukcje: korzystanie z koloru](working-with-color-image-editor-for-icons.md)<br/>
