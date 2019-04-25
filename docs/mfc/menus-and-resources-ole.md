---
title: Menu i zasoby (OLE)
ms.date: 11/04/2016
helpviewer_keywords:
- OLE visual editing servers [MFC]
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- string tables [MFC], visual editing applications
- OLE containers [MFC], menus and resources
- OLE applications [MFC], menus and resources
- OLE server applications [MFC], menus and resources
- toolbars [MFC], OLE document applications
- string editing [MFC], visual editing applications
- server applications [MFC], OLE menus and resources
- applications [OLE], menus and resources
- menus [MFC], OLE document applications
- in-place activation [MFC], OLE menus and resources
- containers [MFC], OLE container applications
- OLE menus and resources [MFC]
ms.assetid: 52bfa086-7d3d-466f-94c7-c7061f3bdb3a
ms.openlocfilehash: 4e8f8c7fa8e24349a741b99822f13d5473373e17
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62225470"
---
# <a name="menus-and-resources-ole"></a>Menu i zasoby (OLE)

Ta grupa artykuły wyjaśnienia dotyczące korzystania z menu i zasoby w aplikacjach dokumentu MFC OLE.

OLE edycja wizualna umieszcza dodatkowymi wymaganiami w menu i innych zasobów, dostarczane przez aplikacje dokumentu OLE, ponieważ istnieje wiele trybów w obu kontenera i aplikacji serwera (składnik) można uruchomić i używane. Na przykład pełny serwer można uruchomić w jednym z tych trzech trybów:

- Autonomiczny.

- W miejscu do edycji w ramach elementu kontenera.

- Otwórz do edycji elementu poza kontekstem swojego kontenera, często w osobnym oknie.

Wymaga to trzy oddzielne menu układy, jeden dla każdego możliwe trybu aplikacji. Tabele akceleratora również są niezbędne dla każdego nowego trybu. Aplikacja kontenera może być lub może nie obsługiwać aktywacji w miejscu, Jeśli tak jest, wymaga nowej struktury menu i skojarzonych tabel akceleratora.

Aktywacja w miejscu wymaga, aby aplikacje kontenera i serwera muszą uzgodnić dla miejsca na pasku menu, pasek narzędzi i stanu. Wszystkie zasoby muszą być zaprojektowane z tym pamiętać. Artykuł [menu i zasoby: Scalanie menu](../mfc/menus-and-resources-menu-merging.md) opisano w tym temacie szczegółowo.

Ze względu na te problemy dokumenty i aplikacje OLE utworzone za pomocą Kreatora aplikacji może mieć maksymalnie cztery oddzielne menu i zasoby tabeli akceleratora. Są one używane w następujących sytuacjach:

|Nazwa zasobu|Zastosowanie|
|-------------------|---------|
|IDR_MAINFRAME|Używane w aplikacji MDI, jeśli plik nie jest otwarty lub w aplikacji interfejsu SDI, niezależnie od tego, otwartych plików. Jest to standardowe menu używanych w aplikacjach innych niż OLE.|
|IDR_\<project>TYPE|Jeśli pliki są otwarte i używane w aplikacji MDI. Używany, gdy aplikacja jest uruchomiona w autonomicznej. Jest to standardowe menu używanych w aplikacjach innych niż OLE.|
|IDR_\<project>TYPE_SRVR_IP|Używane przez serwer lub kontenera, gdy obiekt jest otwarty w miejscu.|
|IDR_\<project>TYPE_SRVR_EMB|Używane przez aplikację serwera, jeśli obiekt zostanie otwarty bez używania aktywacji w miejscu.|

Reprezentuje każda z tych nazw zasobów, menu i zazwyczaj tabeli klawiszy skrótu. Schemat podobne należy używać w aplikacjach MFC, które nie są tworzone za pomocą Kreatora aplikacji.

W następujących artykułach omówiono tematów związanych z kontenerów, serwerów i scalaniem niezbędne do zaimplementowania aktywacji w miejscu menu:

- [Menu i zasoby: Dodatki do kontenera](../mfc/menus-and-resources-container-additions.md)

- [Menu i zasoby: Dodatki do serwera](../mfc/menus-and-resources-server-additions.md)

- [Menu i zasoby: Scalanie menu](../mfc/menus-and-resources-menu-merging.md)

## <a name="see-also"></a>Zobacz także

[OLE](../mfc/ole-in-mfc.md)
