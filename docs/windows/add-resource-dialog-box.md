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
ms.openlocfilehash: c420a1d72aa4ceca7d71840fcccb451b6e0aba0f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857522"
---
# <a name="add-resource-dialog-box"></a>Okno dialogowe dodawania zasobów
Użyj tego okna dialogowego, aby dodać zasoby do projektu aplikacji komputerowych Windows w języku C++.  
  
> [!NOTE]
>  Te informacje nie dotyczą zasobów w aplikacjach platformy uniwersalnej systemu Windows. Aby uzyskać więcej informacji o tym, zobacz [zasobów aplikacji i systemu zarządzania zasobów](/windows/uwp/app-resources/).  
  
 **Typ zasobu**  
 Określa rodzaj zasobu, który chcesz utworzyć.  
  
 Można rozwinąć kursora i okna dialogowe pole zasobu kategorie, aby ujawnić dodatkowych zasobów. Te zasoby znajdują się w programie Visual Studio ...\Microsoft `version`\VC\VCResourceTemplates\\< LCID\>\mfc.rct. Jeśli dodasz .rct — pliki, możesz je umieścić w tym katalogu lub należy określić [zawierają ścieżki](../windows/how-to-specify-include-directories-for-resources.md) dla nich. Zasoby w tych plikach są następnie wyświetlane w drugiej w odpowiedniej kategorii. Nie ma żadnego predefiniowanych limitu liczby .rct — pliki, które można dodać.  
  
 Zasoby, pokazane na najwyższym poziomie w drzewie są domyślne zasoby, które są dostarczane przez program Visual Studio.  
  
 **Nowy**  
 Tworzy zasób zależy od typu wybranego w **typu zasobu** pole. Zasób zostanie otwarty w edytorze odpowiednie. Na przykład w przypadku utworzenia zasobu okna dialogowego, zostanie otwarty w [Edytor okien dialogowych](../windows/dialog-editor.md).  
  
 **Importujuj**  
 Otwiera **zaimportować** okno dialogowe, w którym można przejść do zasobu można czy mają zostać zaimportowane do bieżącego projektu. Możesz zaimportować mapy bitowej, ikona, kursor, plik zasobu HTML, dźwięk (. Plik zasobów WAV), lub pliku niestandardowego zasobu.  
  
 **Niestandardowy**  
 Otwiera [okno dialogowe Nowy zasób niestandardowy](../windows/new-custom-resource-dialog-box.md) , w którym można utworzyć niestandardowego zasobu. Zasoby niestandardowe można edytować w edytorze binarnym tylko.  
  
## <a name="requirements"></a>Wymagania  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: tworzenie zasobu](../windows/how-to-create-a-resource.md)