---
title: 'Aktywacja: zlecenia'
ms.date: 11/04/2016
helpviewer_keywords:
- verbs [MFC]
- OLE [MFC], activation
- edit verb [MFC]
- activation [MFC], verbs
- OLE [MFC], editing
- Primary verb [MFC]
- OLE activation {MFC]
ms.assetid: eb56ff23-1de8-43ad-abeb-dc7346ba7b70
ms.openlocfilehash: f6774f1de1e7abd318e5cd38fed1a2c805270c15
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443332"
---
# <a name="activation-verbs"></a>Aktywacja: zlecenia

W tym artykule opisano play zleceń podstawowych i pomocniczych roli w OLE [aktywacji](../mfc/activation-cpp.md).

Zazwyczaj dwukrotne kliknięcie osadzonego elementu umożliwia użytkownikowi go edytować. Jednak niektóre elementy nie zachowywać się w ten sposób. Na przykład dwukrotnie elementu, który został utworzony za pomocą aplikacji Rejestrator dźwięku nie Otwórz serwer w osobnym oknie; Zamiast tego odtwarza dźwięk.

Przyczyna odpowiadającą tej różnicy zachowanie jest, że elementy Rejestrator dźwięku ma różne "primary — zlecenie." Primary — zlecenie jest akcję wykonywaną, gdy użytkownik kliknie dwukrotnie elementu OLE. Dla większości typów elementów OLE primary — zlecenie jest edycji, który uruchamia serwer, który utworzył element. W przypadku niektórych typów elementów, takich jak elementy Rejestrator dźwięku primary — zlecenie jest Play.

Wiele typów elementów OLE obsługują tylko jeden zlecenie i edycja jest najbardziej popularnym. Jednak niektóre typy elementów obsługują wiele poleceń. Na przykład Rejestrator dźwięku, które obsługują elementy Edytuj jako dodatkowej zlecenie.

Inny zlecenie, często używane jest otwarte. Otwórz zlecenie jest taka sama jak edytowanie, z wyjątkiem aplikacji serwera jest uruchamiany w osobnym oknie. To zlecenie należy używać, gdy aplikacja serwera lub aplikacji kontenera nie obsługuje aktywacji w miejscu.

Wszystkie zlecenia niż primary — zlecenie musi można wywołać za pomocą polecenia podmenu, gdy zaznaczony element. To podmenu zawiera wszystkie zlecenia, które są obsługiwane przez ten element i zwykle jest osiągany przez *typename* **obiektu** polecenie **Edytuj** menu. Instrukcje dotyczące *typename* **obiektu** polecenia, zobacz artykuł [menu i zasoby: dodatki do kontenera](../mfc/menus-and-resources-container-additions.md).

Zlecenia, który obsługuje aplikację serwera są wyświetlane w bazie danych rejestracji Windows. Jeśli aplikacja serwera są zapisywane przy użyciu biblioteki klas Microsoft Foundation, automatycznie zarejestrować wszystkie zlecenia, gdy serwer jest uruchomiony. Jeśli nie, należy go zarejestrować podczas fazy inicjowania aplikacji serwera. Aby uzyskać więcej informacji, zobacz artykuł [rejestracji](../mfc/registration.md).

## <a name="see-also"></a>Zobacz też

[Aktywacja](../mfc/activation-cpp.md)<br/>
[Kontenery](../mfc/containers.md)<br/>
[Serwery](../mfc/servers.md)

