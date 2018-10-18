---
title: Edytor obrazów dla ikon | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/17/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.cursor.F1
- vc.editors.icon.F1
- vc.editors.cursor
- vc.editors.bitmap.F1
dev_langs:
- C++
helpviewer_keywords:
- editors, images
- resource editors [C++], graphics
- Image editor [C++]
- resource editors [C++], Image editor
ms.assetid: 586d2b8b-0348-4883-a85d-1ff0ddbf14dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ecd2b3b94f04a246242a33494a124171e95cae7c
ms.sourcegitcommit: db6b2ad3195e71abfb60b62f3f015f08b0a719d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2018
ms.locfileid: "49410671"
---
# <a name="image-editor-for-icons"></a>Edytor obrazów dla ikon

Po kliknięciu pliku obrazu (na przykład .ico, bmp, PNG) w Eksploratorze rozwiązań obraz, który zostanie otwarty w edytorze obrazu w taki sam sposób, który otwartych plików kodu w edytorze kodu. Gdy karta edytora obrazów jest aktywna, zostanie wyświetlony pasków narzędzi za pomocą wielu narzędzi do tworzenia i edycji obrazów. Oprócz map bitowych, ikon i kursorów można edytować obrazy w formacie GIF lub JPEG przy użyciu poleceń w **obraz** menu i narzędzi na **edytora obrazów** paska narzędzi.

Możliwości Edytora obrazów:

- [Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)

- [Praca z kolorami](../windows/working-with-color-image-editor-for-icons.md)

- [Praca z ikony i kursory: zasoby obrazów do wyświetlania na urządzeniach](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)

- [Korzystanie z klawiszy skrótów dla poleceń edytora obrazów](../windows/accelerator-keys-image-editor-for-icons.md)

**Edytora obrazów** okna wyświetla dwa widoki obrazu, pasek podziału rozdziela dwa okienka. Aby zmieniać względne rozmiary okienek, można przeciągać pasek podziału. Aktywne okienko wyświetla krawędź wyboru.

**Edytora obrazów** okna mogą być dostosowane do potrzeb i preferencji. Możesz [zmienić stopień powiększenia](../windows/changing-the-magnification-factor-image-editor-for-icons.md) i [wyświetlić lub ukryć siatkę pikseli](../windows/displaying-or-hiding-the-pixel-grid-image-editor-for-icons.md).

> [!NOTE]
> Za pomocą **edytora obrazów**, można wyświetlać obrazy 32-bitowe, ale nie można ich edytować.

## <a name="visual-studio-image-library"></a>Biblioteka obrazów programu Visual Studio

Możesz pobrać bezpłatnie **Visual Studio Image Library** zawierającą wiele animacji, bitmap i ikon, których można używać w aplikacjach. Aby uzyskać więcej informacji dotyczących sposobu pobierania biblioteki, zobacz [Biblioteka programu Visual Studio obraz](/visualstudio/designers/the-visual-studio-image-library).

## <a name="managed-resources"></a>Zarządzane zasoby

Możesz użyć **obraz** edytora i [edytorze binarnym](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Edytory zasobów](../windows/resource-editors.md)<br/>
[Ikony](https://msdn.microsoft.com/library/windows/desktop/ms646973.aspx)