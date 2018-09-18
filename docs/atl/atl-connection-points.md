---
title: Punkty połączenia ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- connections, connection points
- ATL, connection points
- connection points [C++], about connection points
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe2cf03debbfd88f19ccc77d3922a9a5c50a50d2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091273"
---
# <a name="atl-connection-points"></a>Punkty połączenia ATL

Obiekt umożliwiający nawiązywanie połączeń jest taki, który obsługuje wychodzących interfejsów. Wychodzące interfejs sprawia, że obiekt do komunikacji z klientem. Dla każdego interfejsu wychodzącego składnika obiekt udostępnia punkt połączenia. Każdy wychodzących interfejs jest implementowany przez klienta do obiektu o nazwie do ujścia.

![Punkty połączenia](../atl/media/vc2zw31.gif "vc2zw31")

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

