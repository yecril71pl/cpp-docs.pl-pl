---
title: Metody tworzenia paska stanu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CStatusBar class [MFC], vs. CStatusBarCtrl
- methods [MFC], creating status bars
- CStatusBarCtrl class [MFC], vs. CStatusBar
- CStatusBarCtrl class [MFC], creating
- methods [MFC]
- status bars [MFC], creating
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 784cd7f5768b899388978e6715ff6ca071bf439e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397880"
---
# <a name="methods-of-creating-a-status-bar"></a>Metody tworzenia paska stanu

Biblioteka MFC zawiera dwie klasy do utworzenia pasków stanu: [CStatusBar](../mfc/reference/cstatusbar-class.md) i [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) (która opakowuje interfejs API sterowania wspólnej Windows). `CStatusBar` zapewnia wszystkie funkcje stanu paska formantu typowego automatycznie współpracuje z usługą menu i paski narzędzi i obsługuje wiele wymagane typowe ustawienia kontroli i struktury dla Ciebie; Jednak wynikowy plik wykonywalny zazwyczaj będzie większy niż utworzony za pomocą `CStatusBarCtrl`.

`CStatusBarCtrl` zwykle powoduje mniejsze pliku wykonywalnego, a może chcieć użyć `CStatusBarCtrl` Jeśli nie zamierzasz przeprowadzić integrację na pasku stanu w architekturę MFC. Jeśli planujesz używać `CStatusBarCtrl` i zintegruj pasek stanu architektury MFC, należy zwrócić uwagę dodatkowe do przedstawiania stanu paska sterowania manipulacje z MFC. Ta informacja nie jest trudne; jest jednak dodatkowej pracy, który jest zbędny w przypadku używania `CStatusBar`.

Visual C++ zapewnia dwa sposoby, aby móc korzystać z formantu typowego paska stanu.

- Utwórz pasek przy użyciu stanu `CStatusBar`, a następnie wywołać [CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl) uzyskać dostęp do `CStatusBarCtrl` funkcji elementów członkowskich.

- Utwórz pasek przy użyciu stanu [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)przez Konstruktor.

Każda z tych metod zapewni Ci dostęp do funkcji Członkowskich formantu paska stanu. Gdy wywołujesz `CStatusBar::GetStatusBarCtrl`, zwraca odwołanie do `CStatusBarCtrl` obiektu, aby można było używać któryś zbiór elementów członkowskich. Zobacz [CStatusBar](../mfc/reference/cstatusbar-class.md) informacji na temat tworzenia i stan paska za pomocą tworzenia `CStatusBar`.

## <a name="see-also"></a>Zobacz też

[Korzystanie ze CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

