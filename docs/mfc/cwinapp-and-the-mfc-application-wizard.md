---
title: Klasa CWinApp i kreator aplikacji MFC
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
ms.openlocfilehash: f57b3b2b37a97093aa6d81b59a12c8cf023e3157
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622939"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>Klasa CWinApp i kreator aplikacji MFC

Podczas tworzenia aplikacji szkieletowej Kreator aplikacji MFC deklaruje klasę aplikacji pochodzącą od [CWinApp](reference/cwinapp-class.md). Kreator aplikacji MFC generuje również plik implementacji zawierający następujące elementy:

- Mapa komunikatów dla klasy aplikacji.

- Pusty Konstruktor klasy.

- Zmienna, która deklaruje jeden i tylko obiekt klasy.

- Standardowa implementacja `InitInstance` funkcji składowej.

Klasa aplikacji jest umieszczana w nagłówku projektu i głównych plikach źródłowych. Nazwy tworzonych klas i plików są oparte na nazwie projektu dostarczanej w Kreatorze aplikacji MFC. Najprostszym sposobem wyświetlania kodu dla tych klas jest [Widok klasy](/visualstudio/ide/viewing-the-structure-of-code).

Dostarczone implementacje standardowe i mapa komunikatów są odpowiednie dla wielu celów, ale można je zmodyfikować w razie potrzeby. Najbardziej interesującymi tymi implementacjami jest `InitInstance` funkcja członkowska. Zazwyczaj należy dodać kod do implementacji szkieletowej `InitInstance` .

## <a name="see-also"></a>Zobacz też

[CWinApp: klasa aplikacji](cwinapp-the-application-class.md)<br/>
[Funkcje składowe CWinApp z możliwością zastąpienia](overridable-cwinapp-member-functions.md)<br/>
[Specjalne usługi CWinApp](special-cwinapp-services.md)
