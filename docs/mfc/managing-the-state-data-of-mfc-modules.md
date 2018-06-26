---
title: Zarządzanie danymi stanu modułów MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- global state [MFC]
- data management [MFC], MFC modules
- window procedure entry points [MFC]
- exported interfaces and global state [MFC]
- module states [MFC], saving and restoring
- data management [MFC]
- MFC, managing state data
- multiple modules [MFC]
- module state restored [MFC]
ms.assetid: 81889c11-0101-4a66-ab3c-f81cf199e1bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5c2bced4f7f04cf75c72e68db0f99e0f89d2566
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930519"
---
# <a name="managing-the-state-data-of-mfc-modules"></a>Zarządzanie danymi stanu modułów MFC
W tym artykule omówiono dane stanu modułów MFC i jak ten stan jest aktualizowany, gdy przepływ wykonania (ścieżka kod ma za pośrednictwem aplikacji podczas wykonywania) uzyskuje i opuszcza modułu. Przełączanie stany modułów z makra afx_manage_state — i method_prologue — również jest omówiona.  
  
> [!NOTE]
>  Termin "module" w tym miejscu odnosi się do programu wykonywalnego lub do biblioteki DLL (lub zestaw biblioteki dll), które działają niezależnie od pozostałej części aplikacji, ale używają kopię udostępnionej biblioteki MFC DLL. Formant ActiveX jest typowym przykładem modułu.  
  
 Jak pokazano na poniższej ilustracji, MFC zawiera dane o stanie dla każdego modułu używane w aplikacji. Dane te przykłady dojść do wystąpienia systemu Windows (używane do ładowania zasobów), wskaźniki do bieżącego `CWinApp` i `CWinThread` obiektów aplikacji, liczby odwołań modułu OLE i różnych map, które utrzymują połączeń między Uchwyty i odpowiadających im wystąpień obiektów MFC obiektów systemu Windows. Jeśli aplikacja używa wielu modułów, dane o stanie każdego modułu nie jest jednak aplikacji szerokości. Zamiast każdy moduł ma własną prywatną kopię danych stanu MFC.  
  
 ![Stan danych pojedynczy moduł &#40;aplikacji&#41;](../mfc/media/vc387n1.gif "vc387n1")  
Dane stanu jednego modułu (aplikacja)  
  
 Dane o stanie modułu jest zawarta w strukturze i jest zawsze dostępna za pośrednictwem wskaźnik do tej struktury. Gdy przepływ wykonania wprowadza danego modułu, jak pokazano na poniższej ilustracji, stan "bieżący" lub "skuteczne" musi mieć stan tego modułu. W związku z tym każdy obiekt wątku ma wskaźnik do struktury skuteczne stan tej aplikacji. Utrzymywanie ten wskaźnik ciągle razy jest niezbędne do zarządzania globalny stan aplikacji i utrzymywanie integralności stan każdego modułu. Zarządzanie niepoprawny stan globalny może spowodować nieprzewidywalne zachowanie aplikacji.  
  
 ![Stan danych wiele modułów](../mfc/media/vc387n2.gif "vc387n2")  
Danymi stanu modułów wielu  
  
 Innymi słowy każdy moduł jest odpowiedzialny za poprawnie przełączanie między stany modułów na wszystkich jego punktów wejścia. "Punkt wejścia" to miejsce, gdy przepływ wykonania można wprowadzić kod modułu. Punkty wejścia obejmują:  
  
-   [Eksportowane funkcje w bibliotece DLL](../mfc/exported-dll-function-entry-points.md)  
  
-   [Funkcje Członkowskie interfejsów modelu COM](../mfc/com-interface-entry-points.md)  
  
-   [Procedury okna](../mfc/window-procedure-entry-points.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)

