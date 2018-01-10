---
title: Sekwencja operacji przy tworzeniu aplikacji OLE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE applications [MFC], creating
- OLE applications [MFC]
- applications [OLE], creating
- applications [OLE]
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: db3b5b9a5f4f62fa71cffa37b30a89aee41fe56f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="sequence-of-operations-for-creating-ole-applications"></a>Sekwencja operacji przy tworzeniu aplikacji OLE
W poniższej tabeli przedstawiono roli i roli w ramach tworzenia OLE łączenie i osadzanie aplikacji. Reprezentuje on opcje dostępne zamiast sekwencji kroki do wykonania.  
  
### <a name="creating-ole-applications"></a>Tworzenie aplikacji OLE  
  
|Zadanie|Jak|Jest w ramach|  
|----------|------------|------------------------|  
|Tworzenie składnika COM.|Kreator aplikacji MFC. Wybierz **pełny serwer** lub **mini serwer** w **Obsługa dokumentów złożonych** kartę.|Platformę generuje szkielet aplikacji z możliwością składnika COM włączone. Wszystkie możliwości COM można przenosić do istniejącej aplikacji tylko niewielką modyfikacji.|  
|Tworzenie aplikacji kontenera od początku.|Kreator aplikacji MFC. Wybierz **kontenera** w **Obsługa dokumentów złożonych** kartę. Korzystając z widoku klasy, przejdź do edytora kodu źródłowego. Wprowadź kod dla funkcji obsługi modelu COM.|Platformę generuje szkielet aplikacji, które można wstawić obiektów COM tworzony przez aplikacje (serwer) składnik COM.|  
|Utwórz aplikację, która obsługuje automatyzacji od początku.|Kreator aplikacji MFC. Wybierz **automatyzacji** z **funkcje zaawansowane** kartę. Za pomocą widoku klasy ujawniać metod i właściwości w aplikacji w celu automatyzacji.|Platformę generuje szkielet aplikacji, która może być aktywowana i automatyzować przez inne aplikacje.|  
  
## <a name="see-also"></a>Zobacz też  
 [Opieranie się na strukturze](../mfc/building-on-the-framework.md)   
 [Sekwencja operacji przy tworzeniu aplikacji MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [Sekwencja operacji przy tworzeniu formantów ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)   
 [Sekwencja operacji przy tworzeniu aplikacji bazy danych](../mfc/sequence-of-operations-for-creating-database-applications.md)

