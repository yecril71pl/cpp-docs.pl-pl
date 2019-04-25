---
title: 'Serwery: Implementowanie serwera'
ms.date: 11/04/2016
helpviewer_keywords:
- servers, implementing
- OLE server applications [MFC], implementing OLE servers
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
ms.openlocfilehash: 953d157f4bbad0b460947740a2622074dfc90f4f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308020"
---
# <a name="servers-implementing-a-server"></a>Serwery: Implementowanie serwera

W tym artykule opisano kod, który tworzy Kreator aplikacji MFC, visual edycji aplikacji serwera. Jeśli nie używasz Kreatora aplikacji, w tym artykule wymieniono obszary, gdzie należy wpisać kod implementujący aplikację serwera.

Korzystając z Kreatora konfiguracji aplikacji do tworzenia nowych aplikacji serwera, zapewnia znaczną ilość kodu specyficznego dla serwera dla Ciebie. W przypadku dodawania visual funkcje edytowania serwer do istniejącej aplikacji musi zduplikowany kod, który Kreator aplikacji czy zostały podane przed dodaniem pozostałej części kodu serwera niezbędne.

Kod serwera, który zawiera Kreatora aplikacji znajduje się na kilka kategorii:

- Definiowanie zasobów serwera:

  - Zasób menu używany, gdy serwer edytuje element osadzony w osobnym oknie.

  - Menu i paski narzędzi zasobów używana, gdy serwer jest aktywny w miejscu.

  Aby uzyskać więcej informacji na temat tych zasobów, zobacz [menu i zasoby: Dodatki do serwera](../mfc/menus-and-resources-server-additions.md).

- Definiowanie klasy elementu pochodną `COleServerItem`. Aby uzyskać więcej szczegółowych informacji dotyczących elementów serwera, zobacz [serwerów: Elementy serwera](../mfc/servers-server-items.md).

- Zmiana klasę bazową klasy dokumentu w celu `COleServerDoc`. Aby uzyskać więcej informacji, zobacz [serwerów: Implementowanie dokumentów serwera](../mfc/servers-implementing-server-documents.md).

- Definiowanie klasy okien ramowych pochodną `COleIPFrameWnd`. Aby uzyskać więcej informacji, zobacz [serwerów: Implementowanie Windows ramowych w miejscu](../mfc/servers-implementing-in-place-frame-windows.md).

- Tworzenie wpisu dla aplikacji serwera w bazie danych rejestracji Windows i rejestrowanie nowego wystąpienia serwera z systemem OLE. Aby uzyskać informacje na ten temat, zobacz [rejestracji](../mfc/registration.md).

- Inicjowanie i uruchamianie aplikacji serwera. Aby uzyskać informacje na ten temat, zobacz [rejestracji](../mfc/registration.md).

Aby uzyskać więcej informacji, zobacz [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerDoc](../mfc/reference/coleserverdoc-class.md), i [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md) w *odwołanie do biblioteki klas*.

## <a name="see-also"></a>Zobacz także

[Serwery](../mfc/servers.md)<br/>
[Kontenery](../mfc/containers.md)<br/>
[Menu i zasoby (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Rejestracja](../mfc/registration.md)
