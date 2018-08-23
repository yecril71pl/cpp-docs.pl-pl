---
title: Okno dialogowe dodawania zasobów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.insertresource
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], adding
- Add Resource dialog box
ms.assetid: e9fb6967-738f-47e8-ab58-728cf35b3af0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a48b99ad1d00fdcc184f6a3fadc772b32057f75d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601333"
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