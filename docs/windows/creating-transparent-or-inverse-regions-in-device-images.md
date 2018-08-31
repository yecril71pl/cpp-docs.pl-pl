---
title: Tworzenie obszarów przezroczystych lub odwróconych w obrazach urządzeń (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cursors [C++], screen regions
- inverse colors, device images
- transparent regions, device images
- transparency, device images
- Image editor [C++], device images
- inverse regions, device images
- cursors [C++], transparent regions
- screen colors
- regions, transparent
- icons [C++], transparent regions
- display devices, transparent and screen regions
- transparent regions in devices
- regions, inverse
- colors [C++], Image editor
- device projects, transparent images
- icons [C++], screen regions
ms.assetid: a994954b-b039-4391-a535-58d1fa10fc3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b5bc95e75cc9a58dd6f01b8a4ca537709941f6bf
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215943"
---
# <a name="creating-transparent-or-inverse-regions-in-device-images-image-editor-for-icons"></a>Tworzenie obszarów przezroczystych lub odwróconych w obrazach urządzeń (Edytor obrazów dla ikon)

W [edytora obrazów](../windows/image-editor-for-icons.md), początkowego obrazu ikony ma atrybut przezroczysty. Chociaż obrazy ikon i kursorów prostokątny, wiele nie są wyświetlane tak ponieważ przezroczysty; części obrazu Pokazuje obrazu podstawowego na ekranie za pomocą ikony lub kursor. Podczas przeciągania ikony części obrazu może pojawić się w kolorze odwrócony. Ten efekt, ustawiając kolor ekranu i odwracanie kolorów w [okno kolorów](../windows/colors-window-image-editor-for-icons.md).

Kolory ekranu i odwrotność, można zastosować do ikony i kursory kształt i kolor obrazu pochodnej albo wyznaczyć odwracanie regionów. Kolory wskazują części obrazu, w czym te atrybuty. Można zmienić kolory, które reprezentują ekranu odwrotność kolorach i atrybuty w edycji. Te zmiany nie wpływają na wygląd ikony lub kursor znajduje się w aplikacji.

> [!NOTE]
> Polecenia menu, zostanie wyświetlony i okien dialogowych mogą różnić się od tych opisanych w **pomocy** w zależności od ustawień aktywnych lub wersji. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

### <a name="to-create-transparent-or-inverse-regions"></a>Aby utworzyć przezroczystych lub odwróconych

1. W **kolory** okna, kliknij przycisk **koloru ekranu** selektora lub **kolor odwrotność** selektora.

2. Zastosuj ekranu lub odwróconych kolorów na obraz przy użyciu narzędzia do rysowania. Aby uzyskać więcej informacji na temat narzędzia do rysowania, zobacz [przy użyciu narzędzia do rysowania](using-a-drawing-tool-image-editor-for-icons.md).

### <a name="to-change-the-screen-or-inverse-color"></a>Aby zmienić kolor ekranu lub odwrotne

1. Wybierz opcję **koloru ekranu** selektora lub **kolor odwrotność** selektora.

2. Wybierz kolor na podstawie **kolory** palety w **kolory** okna.

   Kolor dopełniający automatycznie wyznaczona na potrzeby innych selektora.

   > [!TIP]
   > Po dwukrotnym kliknięciu **koloru ekranu** lub **kolor odwrotność** selektor [okno dialogowe selektora kolorów niestandardowych](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md) pojawia się.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)  
[Ikony i kursory: zasoby obrazów do wyświetlania na urządzeniach](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)