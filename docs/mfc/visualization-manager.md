---
title: Menedżer wizualizacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visualization Manager
ms.assetid: c9dd1365-27ac-42e5-8caa-1004525b4129
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 590c21c3a628af3d8e4c7fc3e5cb0330a0af439a
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123347"
---
# <a name="visualization-manager"></a>Menedżer wizualizacji

Menedżer visual jest obiekt, który określa wygląd całej aplikacji. Działa ona jako pojedyncza klasa gdzie możesz umieścić cały kod rysowania aplikacji. Biblioteki MFC obejmuje kilka menedżerów visual. Można również utworzyć Menedżera visual, aby utworzyć widok niestandardowy dla aplikacji. Na poniższych ilustracjach przedstawiono tej samej aplikacji, gdy włączone są różnych menedżerów visual:

 ![Moja_aplikacja w postaci wyświetlanej przez program CMFCVisualManagerWindows](../mfc/media/vmwindows.png "vmwindows") moja_aplikacja, który używa Menedżera visual program CMFCVisualManagerWindows

 ![Moja_aplikacja w postaci wyświetlanej przez program CMFCVisualManagerVS2005](../mfc/media/vmvs2005.png "vmvs2005") moja_aplikacja, który używa Menedżera visual program CMFCVisualManagerVS2005

 ![Moja_aplikacja w postaci wyświetlanej przez program CMFCVisualManagerOfficeXP](../mfc/media/vmofficexp.png "vmofficexp") moja_aplikacja, który używa Menedżera visual program CMFCVisualManagerOfficeXP

 ![Moja_aplikacja w postaci wyświetlanej przez program CMFCVisualManagerOffice2003](../mfc/media/vmoffice2003.png "vmoffice2003") moja_aplikacja, który używa Menedżera visual program CMFCVisualManagerOffice2003

 ![Moja_aplikacja w postaci wyświetlanej przez program CMFCVisualManagerOffice2007](../mfc/media/msoffice2007.png "msoffice2007") moja_aplikacja, który używa Menedżera visual program CMFCVisualManagerOffice2007

Domyślnie Menedżer visual przechowuje kod rysowania kilku elementów graficznego interfejsu użytkownika. Zapewnienie niestandardowe elementy interfejsu użytkownika, należy zastąpić odpowiednich metod rysowania visual menedżera. Aby uzyskać listę tych metod, zobacz [CMFCVisualManager klasy](../mfc/reference/cmfcvisualmanager-class.md). Metody, które można zastąpić, aby podać niestandardowy wygląd są wszystkie metody, które zaczynają się `OnDraw`.

Aplikacja może mieć tylko jeden `CMFCVisualManager` obiektu. Uzyskanie wskaźnik do Menedżera visual dla aplikacji, wywołaj funkcję statycznych [CMFCVisualManager::GetInstance](../mfc/reference/cmfcvisualmanager-class.md#getinstance). Ponieważ dziedziczy wszystkich menedżerów visual `CMFCVisualManager`, `CMFCVisualManager::GetInstance` — metoda będzie Pobierz wskaźnik do odpowiedniego menedżera visual, nawet w przypadku tworzenia niestandardowych Menedżera visual.

Jeśli chcesz utworzyć niestandardowe Menedżera visual musi on pochodzić od visual menedżera, która już istnieje. Jest domyślną klasę pochodzić z `CMFCVisualManager`. Jednak można użyć innego menedżera visual, jeśli lepiej podobny ma dla aplikacji. Na przykład, jeśli chcesz użyć `CMFCVisualManagerOffice2007` visual manager, ale chce tylko zmienić wygląd separatorów, może pochodzić z klasę niestandardową `CMFCVisualManagerOffice2007`. W tym scenariuszu należy zastąpić tylko metody służące do rysowania separatorów.

Istnieją dwa sposoby, aby użyć konkretnego Menedżera visual dla aplikacji. Jednym ze sposobów jest wywołanie [CMFCVisualManager::SetDefaultManager](../mfc/reference/cmfcvisualmanager-class.md#setdefaultmanager) — metoda i przekazać odpowiednie Menedżera visual jako parametr. Poniższy przykład kodu pokazuje, jak używasz `CMFCVisualManagerVS2005` visual manager przy użyciu tej metody:

```cpp
CMFCVisualManager::SetDefaultManager (RUNTIME_CLASS (CMFCVisualManagerVS2005));
```

Innym sposobem użycia Menedżera visual w aplikacji jest ręcznie utworzyć. Aplikacja będzie używać tego nowego Menedżera visual dla wszystkich renderowania. Jednakże ponieważ może istnieć tylko jedna `CMFCVisualManager` obiekt na aplikację, trzeba będzie usunąć bieżący Menedżer visual przed utworzeniem nowego. W poniższym przykładzie `CMyVisualManager` jest menedżerem visual niestandardowy jest pochodną `CMFCVisualManager`. Następująca metoda ulegnie zmianie, jakie visual manager służy do wyświetlania aplikacji, w zależności od indeksu:

```cpp
void CMyApp::SetSkin (int index)
{
    if (CMFCVisualManager::GetInstance() != NULL)
    {
        delete CMFCVisualManager::GetInstance();
    }

    switch (index)
    {
    case DEFAULT_STYLE: 
        // The following statement creates a new CMFCVisualManager
        CMFCVisualManager::GetInstance();
        break;

    case CUSTOM_STYLE:
        new CMyVisualManager;
        break;

    default:
        CMFCVisualManager::GetInstance();
        break;
    }

    CMFCVisualManager::GetInstance()->RedrawAll();
}
```

## <a name="see-also"></a>Zobacz także

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)  
[Klasa CMFCVisualManager](../mfc/reference/cmfcvisualmanager-class.md)  
