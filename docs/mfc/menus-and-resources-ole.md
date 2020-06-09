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
ms.openlocfilehash: e705f28476df7b594f9648aee8317759211c66c9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626213"
---
# <a name="menus-and-resources-ole"></a>Menu i zasoby (OLE)

W tej grupie artykułów objaśniono korzystanie z menu i zasobów w aplikacjach MFC OLE.

Edycja wizualizacji OLE umieszcza dodatkowe wymagania dotyczące menu i innych zasobów udostępnianych przez aplikacje dokumentów OLE, ponieważ istnieją różne tryby, w których można uruchamiać i używać zarówno aplikacji kontenera, jak i serwera (składników). Na przykład aplikacja całego serwera może działać w jednym z tych trzech trybów:

- Samodzielne.

- W miejscu do edycji elementu w kontekście kontenera.

- Otwórz, aby edytować element poza kontekstem jego kontenera, często w osobnym oknie.

Wymaga to trzech oddzielnych układów menu, po jednym dla każdego możliwego trybu aplikacji. Tabele akceleratorów są również niezbędne dla każdego nowego trybu. Aplikacja kontenera może być nieobsługiwana w przypadku aktywacji w miejscu; Jeśli tak, potrzebuje nowej struktury menu i skojarzonych tabel akceleratorów.

Aktywacja w miejscu wymaga, aby aplikacje kontenera i serwera musiały być negocjowane dla menu, paska narzędzi i przestrzeni pasek stanu. Wszystkie zasoby muszą zostać zaprojektowane z tym zagadnieniem. Menu artykułów [i zasoby: scalanie menu](menus-and-resources-menu-merging.md) obejmuje szczegółowe omówienie tego tematu.

Ze względu na te problemy aplikacje dokumentów OLE utworzone za pomocą Kreatora aplikacji mogą mieć do czterech oddzielnych menu i zasobów tabel akceleratorów. Są one używane z następujących powodów:

|Nazwa zasobu|Użycie|
|-------------------|---------|
|IDR_MAINFRAME|Używane w aplikacji MDI, jeśli żaden plik nie jest otwarty lub w aplikacji SDI niezależnie od otwartych plików. Jest to standardowe menu używane w aplikacjach innych niż OLE.|
|\<project>typ IDR_|Używany w aplikacji MDI, jeśli pliki są otwarte. Używany, gdy aplikacja działa autonomicznie. Jest to standardowe menu używane w aplikacjach innych niż OLE.|
|IDR_ \<project> TYPE_SRVR_IP|Używany przez serwer lub kontener, gdy obiekt jest otwarty.|
|IDR_ \<project> TYPE_SRVR_EMB|Używany przez aplikację serwera, jeśli obiekt jest otwarty bez użycia aktywacji w miejscu.|

Każda z tych nazw zasobów reprezentuje menu i, zazwyczaj, tabelę akceleratora. Podobny schemat powinien być używany w aplikacjach MFC, które nie są tworzone za pomocą Kreatora aplikacji.

W poniższych artykułach omówiono tematy związane z kontenerami, serwerami oraz scalaniem menu, które jest niezbędne do wdrożenia aktywacji w miejscu:

- [Menu i zasoby: dodatki do kontenera](menus-and-resources-container-additions.md)

- [Menu i zasoby: dodatki do serwera](menus-and-resources-server-additions.md)

- [Menu i zasoby: scalanie menu](menus-and-resources-menu-merging.md)

## <a name="see-also"></a>Zobacz też

[OLE](ole-in-mfc.md)
