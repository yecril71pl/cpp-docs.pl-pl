---
title: Klasa CWinApp i kreator aplikacji MFC
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
ms.openlocfilehash: 1a46842d7b4d6a588da585d63e2ad56982bb0ff8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447042"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>Klasa CWinApp i kreator aplikacji MFC

Podczas tworzenia aplikacji szkieletowej Kreator aplikacji MFC deklaruje klasę aplikacji pochodzącą od [CWinApp](../mfc/reference/cwinapp-class.md). Kreator aplikacji MFC generuje również plik implementacji zawierający następujące elementy:

- Mapa komunikatów dla klasy aplikacji.

- Pusty Konstruktor klasy.

- Zmienna, która deklaruje jeden i tylko obiekt klasy.

- Standardowa implementacja funkcji składowej `InitInstance`.

Klasa aplikacji jest umieszczana w nagłówku projektu i głównych plikach źródłowych. Nazwy tworzonych klas i plików są oparte na nazwie projektu dostarczanej w Kreatorze aplikacji MFC. Najprostszym sposobem wyświetlania kodu dla tych klas jest [Widok klasy](/visualstudio/ide/viewing-the-structure-of-code).

Dostarczone implementacje standardowe i mapa komunikatów są odpowiednie dla wielu celów, ale można je zmodyfikować w razie potrzeby. Najbardziej interesujące są te implementacje `InitInstance` funkcji składowej. Zazwyczaj należy dodać kod do implementacji szkieletowej `InitInstance`.

## <a name="see-also"></a>Zobacz też

[CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)<br/>
[Funkcje składowe CWinApp z możliwością zastąpienia](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Specjalne usługi CWinApp](../mfc/special-cwinapp-services.md)
