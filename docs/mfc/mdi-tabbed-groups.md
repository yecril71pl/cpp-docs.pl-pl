---
title: Grupy z kartami MDI
ms.date: 11/04/2016
helpviewer_keywords:
- mdi [MFC], tabbed groups
- tabbed grous [MFC]
ms.assetid: 0a464f36-39b7-4e68-8b67-ec175de28377
ms.openlocfilehash: 0c1bf925003d5081b2cdc837012a57585b1ace60
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624361"
---
# <a name="mdi-tabbed-groups"></a>Grupy z kartami MDI

Funkcja grup z kartami interfejsu wielu dokumentów (MDI) umożliwia aplikacjom wielu dokumentów (MDI) wyświetlanie co najmniej jednego okna z kartami (lub grupą okien z kartami, nazywanych *grupami z kartami*) w obszarze klienta MDI. Okna z kartami można wyrównać w pionie lub w poziomie. Jeśli aplikacja obsługuje więcej niż jedną grupę z kartami MDI, grupy są oddzielane rozdzielaczami.

## <a name="features"></a>Funkcje

Poniżej przedstawiono funkcje grup z kartami MDI:

- Aplikacja może dynamicznie tworzyć okna z kartami.

- Aplikacja może wyrównać okna z tabulacją w poziomie lub w pionie.

- Grupy okien z kartami są rozdzielone rozdzielaczami. Użytkownik może zmieniać rozmiar grup z kartami przy użyciu rozdzielacza.

- Użytkownik może przeciągać poszczególne karty między grupami.

- Użytkownik może przeciągnąć poszczególne karty w celu utworzenia nowych grup.

- Użytkownik może przenosić karty lub tworzyć nowe grupy przy użyciu menu skrótów.

- Aplikacja może zapisywać i ładować układ okien z kartami.

- Aplikacja może zapisywać i ładować listę dokumentów MDI.

- Aplikacja może uzyskiwać dostęp do poszczególnych grup z kartami i modyfikować ich parametry.

### <a name="using-mdi-tabbed-groups"></a>Używanie grup z kartami MDI

Poniżej przedstawiono zadania często wykonywane przy użyciu grup z kartami MDI:

- Aby włączyć grupy z kartami MDI dla głównego okna ramki, wywołaj [CMDIFrameWndEx:: EnableMDITabbedGroups](reference/cmdiframewndex-class.md#enablemditabbedgroups). Drugi parametr tej metody jest wystąpieniem `CMDITabInfo` klasy. Możesz użyć domyślnych parametrów lub zmodyfikować je przed wywołaniem `CMDIFrameWndEx::EnableMDITabbedGroups` .

- Aby zmodyfikować właściwości grupy z kartami MDI w czasie wykonywania, Utwórz lub zmodyfikuj `CMDITabInfo` obiekt i Wywołaj `CMDIFrameWndEx::EnableMDITabbedGroups` ponownie

- Aby uzyskać listę okien z kartami MDI, należy wywołać polecenie `CMDIFrameWndEx::GetMDITabGroups` .

- Aby utworzyć nową grupę z kartami MDI obok aktywnej grupy z kartami, wywołaj polecenie `CMDIFrameWndEx::MDITabNewGroup` .

- Aby przesunąć fokus wprowadzania do poprzedniego lub następnego okna grupy z kartami, wywołaj `CMDIFrameWndEx::MDITabMoveToNextGroup` .

- Aby określić, czy okno jest elementem członkowskim wywołania grupy z kartami MDI `CMDIFrameWndEx::IsMemberOfMDITabGroup` .

- Aby określić, czy karty MDI lub grupy z kartami MDI są włączone dla głównego okna ramki, wywołaj `CMDIFrameWndEx::AreMDITabs` . Aby określić, czy grupy z kartami MDI są włączone, wywołaj `CMDIFrameWndEx::IsMDITabbedGroup` .

- Aby wyświetlić menu skrótów, gdy użytkownik kliknie kartę lub przeciągnie ją do innej grupy z kartami MDI, Przesłoń `CMDIFrameWndEx::OnShowMDITabContextMenu` w `CMDIFrameWndEx` klasie pochodnej. Jeśli ta metoda nie zostanie wdrożona, aplikacja nie wyświetli menu skrótów.

- Aby zapisać układ grup z kartami MDI w aplikacji, wywołaj polecenie `CMDIFrameWndEx::SaveMDIState` . Aby załadować wcześniej zapisany profil grupy z kartami MDI, wywołaj polecenie `CMDIFrameWndEx::LoadMDIState` . Możesz również wywołać te metody, aby załadować lub zapisać listę otwartych dokumentów w aplikacji MDI. Aby uzyskać więcej informacji na temat zapisywania i ładowania stanu MDI, zobacz [CMDIFrameWndEx:: LoadMDIState](reference/cmdiframewndex-class.md#loadmdistate).

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](user-interface-elements-mfc.md)<br/>
[Klasa CMDIFrameWndEx](reference/cmdiframewndex-class.md)<br/>
[Klasa CMDIChildWndEx](reference/cmdichildwndex-class.md)<br/>
[Klasa CMDITabInfo](reference/cmditabinfo-class.md)
