---
title: "Tworzenie aplikacji kontenera dokumentów aktywnych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- active document containers [MFC], creating
- MFC COM, active document containment
- applications [MFC], active document container
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 077d15837ed857ac983c3c9f9d4e7853b45aeee5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-an-active-document-container-application"></a>Tworzenie aplikacji kontenera dokumentów aktywnych
Najprostszym i zalecany sposób tworzenia aplikacji kontenera dokumentów aktywnych jest tworzenie aplikacji kontenera MFC EXE za pomocą Kreatora aplikacji MFC, a następnie zmodyfikować aplikację do obsługi zawieranie dokumentów aktywnych.  
  
#### <a name="to-create-an-active-document-container-application"></a>Do tworzenia aplikacji kontenera dokumentów aktywnych  
  
1.  Z **pliku** menu, kliknij przycisk **projektu**z **nowy** podmenu.  
  
2.  W okienku po lewej stronie kliknij **Visual C++** typu projektu.  
  
3.  Wybierz **aplikacji MFC** w okienku po prawej stronie.  
  
4.  Nazwij projekt `MyProj`, kliknij przycisk **OK**.  
  
5.  Wybierz **Obsługa dokumentów złożonych** strony.  
  
6.  Wybierz **kontenera** lub **kontenera/pełny serwer** opcji.  
  
7.  Wybierz **kontenera dokumentów aktywnych** pole wyboru.  
  
8.  Kliknij przycisk **Zakończ**.  
  
9. Po zakończeniu pracy Kreatora aplikacji MFC generowania aplikacji, należy otworzyć następujące pliki za pomocą Eksploratora rozwiązań:  
  
    -   MyProjview.cpp  
  
10. W MyProjview.cpp wprowadź następujące zmiany:  
  
    -   W `CMyProjView::OnPreparePrinting`, Zastąp zawartość funkcja następującym kodem:  
  
         [!code-cpp[NVC_MFCDocView#56](../mfc/codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]  
  
     `OnPreparePrinting`zapewnia obsługę drukowania. Ten kod zastępuje `DoPreparePrinting`, który jest przygotowanie wydruku domyślne.  
  
     Zawieranie dokumentów aktywnych zapewnia udoskonalony schemat drukowania:  
  
    -   Należy najpierw wywołać aktywnego dokumentu za pomocą jego `IPrint` interfejsu i poinformuj go do samej siebie drukowania. To różni się od poprzedniej zawierania OLE, w kontenerze było renderować obraz zamkniętego elementu do drukarki `CDC` obiektu.  
  
    -   W przypadku niepowodzenia Poinformuj zawartych w niej element, aby wydrukować się za pośrednictwem jego `IOleCommandTarget` — interfejs  
  
    -   W przypadku niepowodzenia należy własne renderowania elementu.  
  
     Statyczne funkcje Członkowskie `COleDocObjectItem::OnPrint` i `COleDocObjectItem::OnPreparePrinting`, zgodnie z implementacją w poprzednim kodzie obsługi tego udoskonalony schemat drukowania.  
  
11. Dodaj implementacji własny i kompilowania aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Zawieranie dokumentów aktywnych](../mfc/active-document-containment.md)

