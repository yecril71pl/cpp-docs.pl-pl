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
ms.openlocfilehash: fce4b036c6a6ae3692353ae02e7d36eb5ddfd1e1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398495"
---
# <a name="visualization-manager"></a>Menedżer wizualizacji

Menedżer visual jest obiektem, który steruje wyglądem całej aplikacji. Działa ona jako pojedyncza klasa gdzie umieścić kod rysowania dla swojej aplikacji. Biblioteka MFC zawiera kilka menedżerów wizualnych. Można również utworzyć visual menedżera, aby utworzyć widok niestandardowy dla swojej aplikacji. Na poniższych ilustracjach przedstawiono tej samej aplikacji, gdy włączone są różnych menedżerów wizualnych:

![MyApp w postaci wyświetlanej przez CMFCVisualManagerWindows](../mfc/media/vmwindows.png "vmwindows") MyApp, który używa Menedżera visual CMFCVisualManagerWindows

![MyApp w postaci wyświetlanej przez CMFCVisualManagerVS2005](../mfc/media/vmvs2005.png "vmvs2005") MyApp, który używa Menedżera visual CMFCVisualManagerVS2005

![MyApp w postaci wyświetlanej przez CMFCVisualManagerOfficeXP](../mfc/media/vmofficexp.png "vmofficexp") MyApp, który używa Menedżera visual CMFCVisualManagerOfficeXP

![MyApp w postaci wyświetlanej przez CMFCVisualManagerOffice2003](../mfc/media/vmoffice2003.png "vmoffice2003") MyApp, który używa Menedżera visual CMFCVisualManagerOffice2003

![MyApp w postaci wyświetlanej przez CMFCVisualManagerOffice2007](../mfc/media/msoffice2007.png "msoffice2007") MyApp, który używa Menedżera visual CMFCVisualManagerOffice2007

Domyślnie visual manager przechowuje kod rysowania dla kilku elementów graficznego interfejsu użytkownika. Aby przekazać niestandardowe elementy interfejsu użytkownika, należy zastąpić powiązane metody rysowania visual menedżera. Aby uzyskać listę tych metod, zobacz [klasa CMFCVisualManager](../mfc/reference/cmfcvisualmanager-class.md). Metody, które można przesłonić, aby zapewnić niestandardowy wygląd są wszystkie metody, które zaczyna się `OnDraw`.

Aplikacja może mieć tylko jeden `CMFCVisualManager` obiektu. Aby uzyskać wskaźnik do Menedżera visual w aplikacji, wywołaj funkcję statyczną [CMFCVisualManager::GetInstance](../mfc/reference/cmfcvisualmanager-class.md#getinstance). Ponieważ dziedziczy wszystkich menedżerów wizualnych `CMFCVisualManager`, `CMFCVisualManager::GetInstance` metody rozpocznie się wskaźnik odpowiednie Menedżera visual, nawet wtedy, gdy tworzysz niestandardowy Menedżer wizualnego.

Jeśli chcesz utworzyć niestandardowe Menedżer wizualnego musi pochodzić z jej z Menedżer wizualnego, który już istnieje. Domyślna klasa wyprowadzenia z jest `CMFCVisualManager`. Jednak można użyć innego menedżera visual, jeśli lepiej przypomina, ma dla aplikacji. Na przykład, jeśli chcieli korzystać z `CMFCVisualManagerOffice2007` Menedżer wizualnego, ale chciała tylko zmienić wygląd separatory, uzyskujesz klasę niestandardową z `CMFCVisualManagerOffice2007`. W tym scenariuszu należy zastąpić tylko metody rysowania separatorów.

Istnieją dwa sposoby, aby użyć konkretnego Menedżera visual w aplikacji. Jednym ze sposobów jest wywołanie [CMFCVisualManager::SetDefaultManager](../mfc/reference/cmfcvisualmanager-class.md#setdefaultmanager) metody i przekazać odpowiednie Menedżera visual jako parametr. Poniższy przykład kodu pokazuje, jak skorzystać z `CMFCVisualManagerVS2005` visual manager przy użyciu tej metody:

```cpp
CMFCVisualManager::SetDefaultManager (RUNTIME_CLASS (CMFCVisualManagerVS2005));
```

Inny sposób, aby użyć Menedżera visual w aplikacji jest utworzenie go ręcznie. Aplikacja będzie używać tego nowego Menedżera visual dla wszystkich renderowania. Jednakże ponieważ może istnieć tylko jeden `CMFCVisualManager` obiektu na aplikację, trzeba będzie usunąć bieżący Menedżera visual, przed utworzeniem nowej. W poniższym przykładzie `CMyVisualManager` jest niestandardowy Menedżer wizualnego, który jest tworzony na podstawie `CMFCVisualManager`. Poniższa metoda zmiany, jakie visual manager służy do wyświetlania aplikacji, w zależności od indeksu:

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

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)<br/>
[Klasa CMFCVisualManager](../mfc/reference/cmfcvisualmanager-class.md)
