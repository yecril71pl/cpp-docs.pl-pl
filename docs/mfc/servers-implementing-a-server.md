---
title: 'Serwery: implementowanie serwera'
ms.date: 11/04/2016
helpviewer_keywords:
- servers, implementing
- OLE server applications [MFC], implementing OLE servers
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
ms.openlocfilehash: a5c89ff1256d557ef417b9e53ce76bbf1b5d6196
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518965"
---
# <a name="servers-implementing-a-server"></a>Serwery: implementowanie serwera

W tym artykule opisano kod, który tworzy Kreator aplikacji MFC, visual edycji aplikacji serwera. Jeśli nie używasz Kreatora aplikacji, w tym artykule wymieniono obszary, gdzie należy wpisać kod implementujący aplikację serwera.

Korzystając z Kreatora konfiguracji aplikacji do tworzenia nowych aplikacji serwera, zapewnia znaczną ilość kodu specyficznego dla serwera dla Ciebie. W przypadku dodawania visual funkcje edytowania serwer do istniejącej aplikacji musi zduplikowany kod, który Kreator aplikacji czy zostały podane przed dodaniem pozostałej części kodu serwera niezbędne.

Kod serwera, który zawiera Kreatora aplikacji znajduje się na kilka kategorii:

- Definiowanie zasobów serwera:

  - Zasób menu używany, gdy serwer edytuje element osadzony w osobnym oknie.

  - Menu i paski narzędzi zasobów używana, gdy serwer jest aktywny w miejscu.

  Aby uzyskać więcej informacji na temat tych zasobów, zobacz [menu i zasoby: dodatki do serwera](../mfc/menus-and-resources-server-additions.md).

- Definiowanie klasy elementu pochodną `COleServerItem`. Aby uzyskać więcej szczegółowych informacji dotyczących elementów serwera, zobacz [serwery: elementy serwera](../mfc/servers-server-items.md).

- Zmiana klasę bazową klasy dokumentu w celu `COleServerDoc`. Aby uzyskać więcej informacji, zobacz [serwery: Implementowanie dokumentów serwera](../mfc/servers-implementing-server-documents.md).

- Definiowanie klasy okien ramowych pochodną `COleIPFrameWnd`. Aby uzyskać więcej informacji, zobacz [serwery: Implementowanie Windows ramki w miejscu](../mfc/servers-implementing-in-place-frame-windows.md).

- Tworzenie wpisu dla aplikacji serwera w bazie danych rejestracji Windows i rejestrowanie nowego wystąpienia serwera z systemem OLE. Aby uzyskać informacje na ten temat, zobacz [rejestracji](../mfc/registration.md).

- Inicjowanie i uruchamianie aplikacji serwera. Aby uzyskać informacje na ten temat, zobacz [rejestracji](../mfc/registration.md).

Aby uzyskać więcej informacji, zobacz [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerDoc](../mfc/reference/coleserverdoc-class.md), i [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md) w *odwołanie do biblioteki klas*.

## <a name="see-also"></a>Zobacz też

[Serwery](../mfc/servers.md)<br/>
[Kontenery](../mfc/containers.md)<br/>
[Menu i zasoby (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Rejestracja](../mfc/registration.md)

