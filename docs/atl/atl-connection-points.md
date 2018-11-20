---
title: Punkty połączenia ATL
ms.date: 11/04/2016
helpviewer_keywords:
- connections, connection points
- ATL, connection points
- connection points [C++], about connection points
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
ms.openlocfilehash: 520537f5d562450dc4ea2a5e5a0c68af513da509
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175059"
---
# <a name="atl-connection-points"></a>Punkty połączenia ATL

Obiekt umożliwiający nawiązywanie połączeń jest taki, który obsługuje wychodzących interfejsów. Wychodzące interfejs sprawia, że obiekt do komunikacji z klientem. Dla każdego interfejsu wychodzącego składnika obiekt udostępnia punkt połączenia. Każdy wychodzących interfejs jest implementowany przez klienta do obiektu o nazwie do ujścia.

![Punkty połączenia](../atl/media/vc2zw31.gif "punkty połączenia")

Każdy punkt połączenia obsługuje [IConnectionPoint](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpoint) interfejsu. Obiekt umożliwiający nawiązywanie połączeń udostępnia punktów połączenia klienta za pośrednictwem [interfejsy IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer) interfejsu.

## <a name="in-this-section"></a>W tej sekcji

[Klasy punktów połączenia ATL](../atl/atl-connection-point-classes.md)<br/>
Krótko opisano klasy ATL, które obsługują punkty połączenia.

[Dodawanie punktów połączenia do obiektu](../atl/adding-connection-points-to-an-object.md)<br/>
Opisano kroki umożliwiają dodawanie punktów połączenia do obiektu.

[Przykład punktu połączenia ATL](../atl/atl-connection-point-example.md)<br/>
Przykład deklarowania punktu połączenia.

## <a name="related-sections"></a>Sekcje pokrewne

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Zawiera łącza do tematów pojęciowych dotyczące programowania przy użyciu biblioteki Active Template Library.

## <a name="see-also"></a>Zobacz też

[Pojęcia](../atl/active-template-library-atl-concepts.md)

