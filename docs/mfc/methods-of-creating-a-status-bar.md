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
ms.openlocfilehash: 9bdaa76dc68467dce1021d9b5f54eaafa248c529
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624272"
---
# <a name="methods-of-creating-a-status-bar"></a>Metody tworzenia paska stanu

MFC udostępnia dwie klasy do tworzenia pasków stanu: [CStatusBar](reference/cstatusbar-class.md) i [CStatusBarCtrl](reference/cstatusbarctrl-class.md) (które zawijają interfejs API usługi Common Control systemu Windows). `CStatusBar`oferuje wszystkie funkcje typowej kontrolki pasek stanu, która automatycznie współdziała z menu i paskami narzędzi, a także obsługuje wiele wymaganych wspólnych ustawień i struktur kontrolek. jednak utworzony plik wykonywalny zwykle będzie większy niż ten, który został utworzony za pomocą programu `CStatusBarCtrl` .

`CStatusBarCtrl`zwykle wynikiem jest mniejszy plik wykonywalny i warto użyć, `CStatusBarCtrl` Jeśli nie zamierzasz zintegrować paska stanu z architekturą MFC. Jeśli planujesz użyć `CStatusBarCtrl` i zintegrować pasek stanu z architekturą MFC, musisz zadbać o to, aby przekazywać manipulowanie formantami paska stanu do MFC. Ta komunikacja nie jest trudna. Jednak w przypadku korzystania z programu jest to dodatkowa niepotrzebna `CStatusBar` .

Visual C++ zapewnia dwa sposoby skorzystania z zalet typowej kontroli nad paskiem stanu.

- Utwórz pasek stanu za pomocą polecenia `CStatusBar` , a następnie Wywołaj [CStatusBar:: GetStatusBarCtrl](reference/cstatusbar-class.md#getstatusbarctrl) , aby uzyskać dostęp do `CStatusBarCtrl` funkcji składowych.

- Utwórz pasek stanu przy użyciu konstruktora [CStatusBarCtrl](reference/cstatusbarctrl-class.md).

Każda z tych metod zapewni dostęp do funkcji Członkowskich kontrolki pasek stanu. Po wywołaniu `CStatusBar::GetStatusBarCtrl` , zwraca odwołanie do `CStatusBarCtrl` obiektu, aby można było użyć dowolnego zestawu funkcji Członkowskich. Zobacz [CStatusBar](reference/cstatusbar-class.md) , aby uzyskać informacje dotyczące konstruowania i tworzenia paska stanu przy użyciu `CStatusBar` .

## <a name="see-also"></a>Zobacz też

[Korzystanie ze CStatusBarCtrl](using-cstatusbarctrl.md)<br/>
[Formanty](controls-mfc.md)
