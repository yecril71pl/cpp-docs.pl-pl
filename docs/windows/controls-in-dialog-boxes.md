---
title: Formanty w oknach dialogowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], dialog boxes
- dialog box controls, about dialog box controls
- dialog box controls
ms.assetid: e216c4f9-2fd4-429d-889a-8ebce7bad177
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 70e3bcfb644893f1dc8b41b9c11a3aee5c92103d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591961"
---
# <a name="controls-in-dialog-boxes"></a>Formanty w oknach dialogowych

Okno dialogowe za pomocą można dodawać formanty [Karta Edytor okien dialogowych](../windows/dialog-editor-tab-toolbox.md) w [okno przybornika](/visualstudio/ide/reference/toolbox), który umożliwia wybranie kontrolki ma i przeciągnij go do okna dialogowego. Domyślnie okno przybornika jest równa Autoukrywanie. Jest wyświetlany jako karty na lewym marginesie rozwiązania, gdy Edytor okien dialogowych jest otwarty. Jednakże, możesz przypiąć **przybornika** okna w miejscu, klikając **Autoukrywanie** przycisk w prawym górnym rogu okna. Aby uzyskać więcej informacji na temat sposobu kontrolowania zachowania tego okna, zobacz [Zarządzanie oknem](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Najszybszym sposobem na dodawanie formantów do okna dialogowego, zmienianie położenia istniejących kontrolek lub przenoszenie formantów w oknie dialogowym do innego, jest metodą przeciągania i upuszczania. Położenie kontrolki jest opisany w linia kropkowana, dopóki nie zostanie usunięte w oknie dialogowym. Po dodaniu kontrolki do okna dialogowego za pomocą metody przeciągania i upuszczania kontrolki otrzymuje standardową wysokość odpowiednie dla tego typu kontrolki.

Podczas dodawania kontrolki do okna dialogowego lub zmienić jej położenie, jego położenie końcowego może zależeć od prowadnice i marginesy, czy należy wprowadzić jakieś siatki układu włączona.

Po dodaniu kontrolki do okna dialogowego, można zmienić właściwości, takie jak jego podpis w [okno właściwości](/visualstudio/ide/reference/properties-window). Można wybrać wiele kontrolek i zmiany ich właściwości wszystkie na raz.

- [Dodawanie, edytowanie lub usuwanie kontrolek](adding-editing-or-deleting-controls.md)

- [Zaznaczanie kontrolek](../windows/selecting-controls.md)

- [Ustalanie rozmiaru pojedynczych kontrolek](../windows/sizing-individual-controls.md)

- [Tworzenie kontrolek o tej samej szerokości, wysokości lub o tym samym rozmiarze](../windows/making-controls-the-same-width-height-or-size.md)

- [Ustawianie rozmiaru pola kombi i jego listy rozwijanej](setting-the-size-of-the-combo-box-and-its-drop-down-list.md)

- [Dodawanie wartości do kontrolki pola kombi](../windows/adding-values-to-a-combo-box-control.md)

- [Ustawianie szerokości poziomego paska przewijania](../windows/setting-the-width-of-a-horizontal-scroll-bar.md)

- [Rozmieszczenie kontrolek w oknach dialogowych](../windows/arrangement-of-controls-on-dialog-boxes.md)

- [Kontrolki niestandardowe w Edytorze okien dialogowych](custom-controls-in-the-dialog-editor.md)

- [Definiowanie mnemonik (klucze dostępu)](../windows/defining-mnemonics-access-keys.md)

- [Określanie lokalizacji i rozmiaru okna dialogowego](../windows/specifying-the-location-and-size-of-a-dialog-box.md)

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Dodawanie obsługi zdarzeń dla kontrolek okna dialogowego](../windows/adding-event-handlers-for-dialog-box-controls.md)  
[Kontrolki okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md)  
[Edytor okien dialogowych](../windows/dialog-editor.md)