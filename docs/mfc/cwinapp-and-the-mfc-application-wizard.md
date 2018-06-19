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
ms.openlocfilehash: d40f314c7717d2e69b2b4802bf9c2c5468511db5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341264"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>Klasa CWinApp i kreator aplikacji MFC
Podczas tworzenia szkielet aplikacji, Kreator aplikacji MFC deklaruje pochodną klasy aplikacji [CWinApp](../mfc/reference/cwinapp-class.md). Kreator aplikacji MFC także generuje plik implementacji, który zawiera następujące elementy:  
  
-   Mapy komunikatów dla klasy aplikacji.  
  
-   Konstruktor klasy puste.  
  
-   Zmienna, która deklaruje jeden i tylko obiekt wybranej klasy.  
  
-   Standardowa implementacja elementu z `InitInstance` funkcję elementu członkowskiego.  
  
 Klasa aplikacji znajduje się w nagłówku projektu i plików źródłowych głównego. Nazwy klas i pliki tworzone są oparte na nazwę projektu, podane w Kreator aplikacji MFC. Najprostszym sposobem na wyświetlenie kodu dla tych klas jest za pośrednictwem [widoku klasy](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925).  
  
 Implementacje standardowe i mapy komunikatów dostarczonych są odpowiednie dla wielu celów, ale można je zmodyfikować zgodnie z potrzebami. Najbardziej interesujące tych implementacji jest `InitInstance` funkcję elementu członkowskiego. Zazwyczaj dodasz kod do implementacji szkieletowych `InitInstance`.  
  
## <a name="see-also"></a>Zobacz też  
 [CWinApp: Klasa aplikacji](../mfc/cwinapp-the-application-class.md)   
 [Funkcje Członkowskie CWinApp z możliwością zastąpienia](../mfc/overridable-cwinapp-member-functions.md)   
 [Specjalne usługi CWinApp](../mfc/special-cwinapp-services.md)

