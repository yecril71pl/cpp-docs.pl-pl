---
title: Okno dialogowe dodawania zasobów (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.insertresource
helpviewer_keywords:
- resources [C++], adding
- Add Resource dialog box [C++]
ms.assetid: e9fb6967-738f-47e8-ab58-728cf35b3af0
ms.openlocfilehash: b20ec4a076e276c905a96c2deabd619ea10517f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503131"
---
# <a name="add-resource-dialog-box"></a>Okno dialogowe dodawania zasobów

To okno dialogowe służy do dodawania zasobów do projektu aplikacji pulpitu Windows w języku C++.

> [!NOTE]
> Te informacje nie ma zastosowania do zasobów w aplikacjach platformy uniwersalnej Windows. Aby uzyskać więcej informacji o tym, zobacz [zasobów aplikacji i systemu zarządzania zasobów](/windows/uwp/app-resources/).

### <a name="resource-type"></a>Typ zasobu

Określa rodzaj zasobu, który chcesz utworzyć.

Można rozwinąć kursora i okna dialogowego pole zasobów kategorie, aby ujawnić dodatkowe zasoby. Te zasoby znajdują się w programie Visual Studio ...\Microsoft `version`\VC\VCResourceTemplates\\< LCID\>\mfc.rct. Jeśli dodasz .rct — pliki, należy je umieścić w tym katalogu lub należy określić [ścieżki dołączania](../windows/how-to-specify-include-directories-for-resources.md) dla nich. Zasoby w tych plikach są następnie wyświetlane na drugim poziomie do odpowiedniej kategorii. Nie ma żadnych wstępnie limitu liczby .rct — pliki, które można dodać.

Zasoby pokazane na najwyższym poziomie w drzewie są domyślne zasoby, które są dostarczane przez program Visual Studio.

### <a name="new"></a>New

Tworzy zasób, w zależności od typu wybranego na liście **typ zasobu** pole. Zasób zostanie otwarty w edytorze odpowiednie. Na przykład, jeśli tworzysz zasobu okna dialogowego, zostanie on otwarty w [Edytor okien dialogowych](../windows/dialog-editor.md).

### <a name="import"></a>{1&gt;Importuj&lt;1}

Otwiera **zaimportować** okno dialogowe, w którym możesz przejść do zasobu należy czy mają zostać zaimportowane do bieżącego projektu. Możesz zaimportować mapy bitowej, ikony, kursor, plik zasobu HTML, dźwięk (. Plik zasobów WAV) lub plik zasobów niestandardowych.

### <a name="custom"></a>Niestandardowe

Otwiera [okno dialogowe Nowy zasób niestandardowy](../windows/new-custom-resource-dialog-box.md) , w którym możesz tworzyć zasobów niestandardowych. Zasoby niestandardowe można edytować w edytorze binarnym tylko.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Instrukcje: tworzenie zasobu](../windows/how-to-create-a-resource.md)