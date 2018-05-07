---
title: Wstawianie formularza do projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e62618301e09ad4c44fb91608976ecab972a59da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="inserting-a-form-into-a-project"></a>Wstawianie formularza do projektu
Formularze zapewniają wygodne kontenera formantów. Można łatwo wstawiać formularzy MFC do aplikacji, tak długo, jak aplikacja obsługuje biblioteki MFC.  
  
### <a name="to-insert-a-form-into-your-project"></a>Aby wstawić formularza do projektu  
  
1.  Z widoku klasy wybierz projekt, do której chcesz dodać formularz, a następnie kliknij prawym przyciskiem myszy.  
  
2.  W menu skrótów kliknij **Dodaj** , a następnie kliknij przycisk **Dodaj klasę**.  
  
     Jeśli **nowy formularz** polecenie jest niedostępne, projekt może być oparty na Active Template Library (ATL). Aby dodać Projekt ATL formularza, należy najpierw [określić pewne ustawienia](../atl/reference/application-settings-atl-project-wizard.md) tworząc po raz pierwszy projekt.  
  
3.  Z **MFC** folderu, kliknij przycisk **klasy MFC**.  
  
4.  Za pomocą Kreator klas MFC, wykonaj nową klasę pochodną [CFormView](../mfc/reference/cformview-class.md).  
  
 Visual C++ dodaje formularza do aplikacji, otwieranie wewnątrz edytora okien dialogowych, tak aby mogli rozpocząć dodawanie formantów i pracy z całego projektu.  
  
 Można wykonać następujące czynności dodatkowe (nie dotyczy aplikacji opartych na oknach dialogowych):  
  
1.  Zastąpienie `OnUpdate` funkcję elementu członkowskiego.  
  
2.  Wdrożenie funkcją członkowską, aby przenieść dane z widoku do dokumentu.  
  
3.  Utwórz `OnPrint` funkcję elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Widoki formularzy](../mfc/form-views-mfc.md)

