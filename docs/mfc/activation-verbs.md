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
ms.openlocfilehash: 03edba0a4336fdc147ef6dd10c7a8154aca19d3a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616645"
---
# <a name="activation-verbs"></a>Aktywacja: zlecenia

W tym artykule wyjaśniono, że główne i pomocnicze zlecenia są odtwarzane w ramach [aktywacji](activation-cpp.md)OLE.

Zazwyczaj dwukrotne kliknięcie elementu osadzonego umożliwia użytkownikowi edycję. Jednak niektóre elementy nie działają w ten sposób. Na przykład dwukrotne kliknięcie elementu utworzonego za pomocą aplikacji rejestratora dźwięku nie powoduje otwarcia serwera w osobnym oknie; Zamiast tego odtwarza dźwięk.

Przyczyną tego zachowania jest różnica polega na tym, że elementy rejestratora dźwięku mają inne "podstawowe zlecenie". Zlecenie podstawowe jest akcją wykonywaną, gdy użytkownik kliknie dwukrotnie element OLE. W przypadku większości typów elementów OLE zlecenie podstawowe jest Edytuj, co spowoduje uruchomienie serwera, który utworzył element. W przypadku niektórych typów elementów, takich jak elementy rejestratora dźwięku, zlecenie podstawowe jest odtwarzane.

Wiele typów elementów OLE obsługuje tylko jedno zlecenie, a Edycja jest najbardziej powszechną. Jednak niektóre typy elementów obsługują wiele zleceń. Na przykład elementy rejestratora dźwięku obsługują edytowanie jako zlecenie pomocnicze.

Używane jest często inne zlecenie. Otwarte zlecenie jest identyczne z edytowaniem, z tą różnicą, że aplikacja serwera jest uruchamiana w osobnym oknie. Tego zlecenia należy używać, gdy aplikacja kontenera lub aplikacja serwera nie obsługuje aktywacji w miejscu.

Wszystkie czasowniki inne niż zlecenia podstawowe muszą być wywoływane za pomocą polecenia podmenu, gdy element jest zaznaczony. To podmenu zawiera wszystkie czasowniki obsługiwane przez element i jest zazwyczaj osiągane przez polecenie *typename* **obiektu** TypeName w menu **Edycja** . Aby uzyskać informacje na temat polecenia **obiektu** *TypeName* , zobacz [menu artykułów i zasoby: Dodatki do kontenera](menus-and-resources-container-additions.md).

Zlecenia obsługiwane przez aplikację serwera są wymienione w bazie danych rejestracji systemu Windows. Jeśli aplikacja serwera jest zapisywana biblioteka MFC, wszystkie zlecenia zostaną automatycznie zarejestrowane po uruchomieniu serwera. W przeciwnym razie należy je zarejestrować podczas fazy inicjowania aplikacji serwera. Aby uzyskać więcej informacji, zobacz [rejestracja](registration.md)artykułu.

## <a name="see-also"></a>Zobacz też

[Uaktywnienie](activation-cpp.md)<br/>
[Containers](containers.md)<br/>
[Serwery](servers.md)
