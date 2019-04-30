---
title: Metody tworzenia paska narzędzi
ms.date: 11/04/2016
helpviewer_keywords:
- CToolBarCtrl class [MFC], and CToolBar class [MFC]
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- toolbar controls [MFC]
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
ms.openlocfilehash: f269ad990042f51554ec598b0bddbe5a6d7776b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383928"
---
# <a name="methods-of-creating-a-toolbar"></a>Metody tworzenia paska narzędzi

Biblioteka MFC zawiera dwie klasy do utworzenia pasków narzędzi: [CToolBar](../mfc/reference/ctoolbar-class.md) i [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) (która opakowuje interfejs API sterowania wspólnej Windows). `CToolBar` zapewnia wszystkie funkcje formantu typowego paska narzędzi i obsługuje wiele wymagane typowe ustawienia kontroli i struktury dla Ciebie; Jednak wynikowy plik wykonywalny zazwyczaj będzie większy niż utworzony za pomocą `CToolBarCtrl`.

`CToolBarCtrl` zwykle powoduje mniejsze pliku wykonywalnego, a może chcieć użyć `CToolBarCtrl` Jeśli nie zamierzasz integrowanie narzędzi architektury MFC. Jeśli planujesz używać `CToolBarCtrl` i integrowanie narzędzi architektury MFC, należy zwrócić uwagę dodatkowe do komunikowania się manipulacje formantu paska narzędzi z MFC. Ta informacja nie jest trudne; jest jednak dodatkowej pracy, który jest zbędny w przypadku używania `CToolBar`.

Visual C++ zapewnia dwa sposoby, aby móc korzystać z formantu typowego paska narzędzi.

- Utworzyć przy użyciu narzędzi `CToolBar`, a następnie wywołaj [CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl) uzyskać dostęp do `CToolBarCtrl` funkcji elementów członkowskich.

- Tworzenie za pomocą narzędzi [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)przez Konstruktor.

Każda z tych metod zapewni Ci dostęp do funkcji Członkowskich z formantem paska narzędzi. Gdy wywołujesz `CToolBar::GetToolBarCtrl`, zwraca odwołanie do `CToolBarCtrl` obiektu, aby można było używać któryś zbiór elementów członkowskich. Zobacz [CToolBar](../mfc/reference/ctoolbar-class.md) informacji na temat tworzenia i utworzenie przy użyciu narzędzi `CToolBar`.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
