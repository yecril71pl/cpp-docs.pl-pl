---
title: Klawisze skrótów (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f211b15134ad292c9e7e4d3ed92d81ea59dd3b86
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43683303"
---
# <a name="accelerator-keys-image-editor-for-icons"></a>Klawisze skrótów (Edytor obrazów dla ikon)

Poniżej przedstawiono klawisze skrótów dla poleceń edytora obrazów, które są powiązane z kluczy domyślnie. Aby zmienić klawisze skrótów, kliknij przycisk **opcje** na **narzędzia** menu, a następnie wybierz **klawiatury** w obszarze **środowiska** folderu. Aby uzyskać więcej informacji, zobacz [określenie i dostosowywanie skrótów klawiaturowych](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

> [!NOTE]
> Dostępne opcje w oknach dialogowych i nazwy i lokalizacje poleceń menu, który zostanie wyświetlony, mogą różnić się od opisanych w pomocy, w zależności od ustawień aktywnych lub wersji. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

|Polecenie|klucze|Opis|
|-------------|----------|-----------------|
|Image.AirBrushTool|**CTRL** + **A**|Rysuje za pomocą aerografu o wybranym rozmiarze i kolorze.|
|Image.BrushTool|**CTRL** + **B**|Rysuje pędzlem o wybranym kształcie, rozmiarze i kolorze.|
|Image.CopyAndOutlineSelection|**CTRL** + **Shift** + **U**|Tworzy kopię bieżącego zaznaczenia i zakreśla ją. Jeśli kolor tła znajduje się w bieżącym zaznaczeniu, będzie on wykluczony, jeśli masz [przezroczyste](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) wybrane.|
|Image.DrawOpaque|**CTRL** + **"j"**|Sprawia, że bieżące zaznaczenie albo [przezroczystości](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|
|Image.EllipseTool|**CTRL** + **P**|Rysuje elipsę o wybranej szerokości linii i kolorze.|
|Image.EraserTool|**CTRL** + **Shift** + **I**|Wymazuje część obrazu (z bieżącym kolorem tła).|
|Image.FilledEllipseTool|**CTRL** + **Shift** + **Alt** + **P**|Rysuje wypełnioną elipsę.|
|Image.FilledRectangleTool|**CTRL** + **Shift** + **Alt** + **R**|Rysuje wypełniony prostokąt.|
|Image.FilledRoundRectangleTool|**CTRL** + **Shift** + **Alt** + **W**|Rysuje wypełniony prostokąt zaokrąglony.|
|Image.FillTool|**CTRL** + **F**|Wypełnia obszar.|
|Image.FlipHorizontal|**CTRL** + **H**|Przerzuca obraz lub zaznaczenie w poziomie.|
|Image.FlipVertical|**SHIFT**+ **Alt** + **H**|Przerzuca obraz lub zaznaczenie w pionie.|
|Image.LargerBrush|**CTRL** + **=**|Zwiększa rozmiar pędzla o jeden piksel w każdym kierunku. Aby zmniejszyć rozmiar pędzla, zobacz opis polecenia Image.SmallerBrush w tej tabeli.|
|Image.LineTool|**CTRL** + **L**|Rysuje linię prostą o wybranym kształcie, rozmiarze i kolorze.|
|Image.MagnificationTool|**CTRL** + **M**|Aktywuje **Magnify** narzędzia, które umożliwia powiększanie określonych fragmentów obrazu.|
|Image.Magnify|**CTRL** + **Shift** + **M**|Przełącza pomiędzy bieżącym powiększeniem i powiększeniem 1:1.|
|Image.NewImageType|**Wstaw**|Uruchamia [New \<urządzenia > okno dialogowe typu obrazu](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md) za pomocą którego można utworzyć obrazu dla typu inny obraz.|
|Image.NextColor|**CTRL** + **]**<br /><br /> - lub -<br /><br /> **CTRL** + **Strzałka w prawo**|Zmienia kolor pierwszego planu rysunku na następny kolor z palety.|
|Image.NextRightColor|**CTRL** + **Shift** + **]**<br /><br /> - lub -<br /><br /> **SHIFT** + **Ctrl** + **Strzałka w prawo**|Zmienia kolor tła rysunku na następny kolor z palety.|
|Image.OutlinedEllipseTool|**SHIFT** + **Alt** + **P**|Rysuje wypełnioną elipsę z konturem.|
|Image.OutlinedRectangleTool|**SHIFT** + **Alt** + **R**|Rysuje wypełniony prostokąt z konturem|
|Image.OutlinedRoundRectangleTool|**SHIFT** + **Alt** + **W**|Rysuje wypełniony prostokąt zaokrąglony z konturem.|
|Image.PencilTool|**CTRL** + **I**|Rysuje za pomocą jednopikselowego ołówka.|
|Image.PreviousColor|**CTRL** + **[**<br /><br /> - lub -<br /><br /> **CTRL** + **Strzałka w lewo**|Zmienia kolor pierwszego planu rysunku na poprzedni kolor z palety.|
|Image.PreviousRightColor|**CTRL** + **Shift** + **[**<br /><br /> - lub -<br /><br /> **SHIFT** + **Ctrl** + **Strzałka w lewo**|Zmienia kolor tła rysunku na poprzedni kolor z palety.|
|Image.RectangleSelectionTool|**SHIFT** + **Alt** + **S**|Wybiera prostokątny fragment obrazu do przesunięcia, skopiować lub edycji.|
|Image.RectangleTool|ALT + R|Rysuje prostokąt o wybranej szerokości linii i kolorze.|
|Image.Rotate90Degrees|**CTRL** + **Shift** + **H**|Obraca obraz lub zaznaczenie o 90 stopni.|
|Image.RoundedRectangleTool|**ALT** + **W**|Rysuje prostokąt zaokrąglony o wybranej szerokości linii i kolorze.|
|Image.ShowGrid|**CTRL** + **Alt** + **S**|Włącza/wyłącza siatkę pikseli (zaznacza lub czyści **siatkę pikseli** opcji [okno dialogowe Ustawienia siatki](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|
|Image.ShowTileGrid|**CTRL** + **Shift** + **Alt** + **S**|Włącza/wyłącza siatkę kafelków (zaznacza lub czyści **siatka** opcji [okno dialogowe Ustawienia siatki](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|
|Image.SmallBrush|**Ctrl** + **.** (okres)|Zmniejsza **pędzla** rozmiar do jednego piksela. (Zobacz też polecenia Image.LargerBrush i Image.SmallerBrush w tej tabeli).|
|Image.SmallerBrush|**CTRL**  +  **-** (minus)|Zmniejsza rozmiar pędzla o jeden piksel w każdym kierunku. Aby ponownie zwiększyć rozmiar pędzla, zobacz opis polecenia Image.LargerBrush w tej tabeli.|
|Image.TextTool|**CTRL** + **T**|Otwiera [okno dialogowe narzędzie tekstowe](../windows/text-tool-dialog-box-image-editor-for-icons.md).|
|Image.UseSelectionAsBrush|**CTRL** + **U**|Rysuje, używając bieżącego zaznaczenia jako pędzla.|
|Image.ZoomIn|**CTRL** + **Shift** + **.** (okres)<br /><br /> - lub -<br /><br /> **CTRL** + **Strzałka w górę**|Zwiększa powiększenie bieżącego widoku.|
|Image.ZoomOut|**CTRL** + **,** (przecinek)<br /><br /> - lub -<br /><br /> **CTRL** + **strzałkę w dół**|Zmniejsza powiększenie bieżącego widoku.|

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)