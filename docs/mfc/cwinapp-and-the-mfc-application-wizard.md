---
title: Klasa CWinApp i Kreator aplikacji MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWinApp
dev_langs:
- C++
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 009126061856d1165e5d08f6ecc4bd2e7745f2fd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382963"
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

