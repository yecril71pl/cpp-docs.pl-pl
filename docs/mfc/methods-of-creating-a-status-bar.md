---
title: Metody tworzenia paska stanu
ms.date: 11/04/2016
helpviewer_keywords:
- CStatusBar class [MFC], vs. CStatusBarCtrl
- methods [MFC], creating status bars
- CStatusBarCtrl class [MFC], vs. CStatusBar
- CStatusBarCtrl class [MFC], creating
- methods [MFC]
- status bars [MFC], creating
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
ms.openlocfilehash: a2301301d0012bd93ffedd0452dec140174402e0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276887"
---
# <a name="methods-of-creating-a-status-bar"></a>Metody tworzenia paska stanu

Biblioteka MFC zawiera dwie klasy do utworzenia pasków stanu: [CStatusBar](../mfc/reference/cstatusbar-class.md) i [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) (która opakowuje interfejs API sterowania wspólnej Windows). `CStatusBar` zapewnia wszystkie funkcje stanu paska formantu typowego automatycznie współpracuje z usługą menu i paski narzędzi i obsługuje wiele wymagane typowe ustawienia kontroli i struktury dla Ciebie; Jednak wynikowy plik wykonywalny zazwyczaj będzie większy niż utworzony za pomocą `CStatusBarCtrl`.

`CStatusBarCtrl` zwykle powoduje mniejsze pliku wykonywalnego, a może chcieć użyć `CStatusBarCtrl` Jeśli nie zamierzasz przeprowadzić integrację na pasku stanu w architekturę MFC. Jeśli planujesz używać `CStatusBarCtrl` i zintegruj pasek stanu architektury MFC, należy zwrócić uwagę dodatkowe do przedstawiania stanu paska sterowania manipulacje z MFC. Ta informacja nie jest trudne; jest jednak dodatkowej pracy, który jest zbędny w przypadku używania `CStatusBar`.

Visual C++ zapewnia dwa sposoby, aby móc korzystać z formantu typowego paska stanu.

- Utwórz pasek przy użyciu stanu `CStatusBar`, a następnie wywołać [CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl) uzyskać dostęp do `CStatusBarCtrl` funkcji elementów członkowskich.

- Utwórz pasek przy użyciu stanu [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)przez Konstruktor.

Każda z tych metod zapewni Ci dostęp do funkcji Członkowskich formantu paska stanu. Gdy wywołujesz `CStatusBar::GetStatusBarCtrl`, zwraca odwołanie do `CStatusBarCtrl` obiektu, aby można było używać któryś zbiór elementów członkowskich. Zobacz [CStatusBar](../mfc/reference/cstatusbar-class.md) informacji na temat tworzenia i stan paska za pomocą tworzenia `CStatusBar`.

## <a name="see-also"></a>Zobacz także

[Korzystanie ze CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
