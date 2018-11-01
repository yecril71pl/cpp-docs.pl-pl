---
title: Klasa CWinApp i kreator aplikacji MFC
ms.date: 11/04/2016
f1_keywords:
- CWinApp
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
ms.openlocfilehash: c659387043accbd6cdad7d5e2b97ce8bf15c6e63
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437210"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>Klasa CWinApp i kreator aplikacji MFC

Podczas tworzenia szkielet aplikacji, Kreator aplikacji MFC deklaruje pochodną klasę aplikacji [CWinApp](../mfc/reference/cwinapp-class.md). Kreator aplikacji MFC generuje również plik implementacji, który zawiera następujące elementy:

- Mapy komunikatów dla klasy aplikacji.

- Konstruktor pustą klasę.

- Zmienna, która deklaruje tylko obiekt klasy.

- Standardowa implementacja usługi `InitInstance` funkcja elementu członkowskiego.

Klasa aplikacji znajduje się w nagłówku projektu i plików źródłowych głównego. Nazwy klasy i pliki tworzone są oparte na nazwę projektu, który podasz w Kreatorze aplikacji MFC. Najprostszym sposobem, aby wyświetlić kod dla tych klas jest za pośrednictwem [Widok klas](/visualstudio/ide/viewing-the-structure-of-code).

Standardowe wdrożenia i mapy wiadomości podano są odpowiednie dla wielu celów, ale możesz modyfikować je stosownie do potrzeb. Najbardziej interesujące tych implementacji `InitInstance` funkcja elementu członkowskiego. Zazwyczaj należy dodać kod do implementacji szkieletowych `InitInstance`.

## <a name="see-also"></a>Zobacz też

[CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)<br/>
[Funkcje składowe CWinApp z możliwością zastąpienia](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Specjalne usługi CWinApp](../mfc/special-cwinapp-services.md)

