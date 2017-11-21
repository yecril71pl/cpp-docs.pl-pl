---
title: "Porady: Konwertowanie istniejącej wstążki MFC na zasób wstążki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ribbon resource, converting from an MFC ribbon
- MFC ribbon, converting to a ribbon resource
ms.assetid: 324b7ff6-58f9-4691-96a9-9836a79d0fb6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 97097618ee3f166866daad68190b7c22cca3c16d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource"></a>Porady: konwertowanie istniejącej wstążki MFC na zasób wstążki
Wstążka zasoby są łatwiejsze do wizualizacji, modyfikowania i obsłudze niż wstążek kodowane ręcznie. W tym temacie opisano, jak przekonwertować kodowane ręcznie wstążki w projektach MFC na zasób wstążki.  
  
 Musi mieć istniejący projekt MFC, zawierający kod, który używa klas wstążki MFC, na przykład [CMFCRibbonBar klasy](../mfc/reference/cmfcribbonbar-class.md).  
  
### <a name="to-convert-an-mfc-ribbon-to-a-ribbon-resource"></a>Aby przekonwertować wstążki MFC na zasób wstążki  
  
1.  W programie Visual Studio w istniejącego projektu MFC, otwórz plik źródłowy, gdy obiekt CMFCRibbonBar został zainicjowany. Plik jest zazwyczaj mainfrm.cpp. Dodaj następujący kod po kodzie inicjowania dla wstążki.  
  
 ```  
    m_wndRibbonBar.SaveToXMLFile("RibbonOutput.xml");

 ```  
  
     Zapisz i zamknij plik.  
  
2.  Tworzenie i uruchamianie aplikacji MFC, a następnie w programie Notatnik Otwórz RibbonOutput.txt i skopiować jego zawartość.  
  
3.  W programie Visual Studio na **projektu** menu, kliknij przycisk **dodawania zasobów**. W **dodawania zasobów** okno dialogowe, wybierz opcję **wstążki** , a następnie kliknij przycisk **nowy**.  
  
     Visual Studio tworzy zasób Wstążki i otwarcie go w widoku Projekt. Identyfikator zasobu wstążki jest IDR_RIBBON1, która jest wyświetlana w **widok zasobów**. Wstążka jest zdefiniowana w pliku XML ribbon1.mfcribbon ms.  
  
4.  W programie Visual Studio Otwórz ribbon1.mfcribbon ms, usuń jego zawartość, a następnie wklej zawartość RibbonOutput.txt, które wcześniej zostały skopiowane. Zapisz i zamknij ribbon1.mfcribbon ms.  
  
5.  Ponownie otworzyć pliku źródłowego, gdy obiekt CMFCRibbonBar został zainicjowany (zazwyczaj mainfrm.cpp) i Oznacz jako komentarz istniejącej wstążki kodu. Dodaj następujący kod po kodzie zostanie oznaczone jako komentarz.  
  
 ```  
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);

 ```  
  
6.  Skompiluj projekt i uruchomić program.  
  
## <a name="see-also"></a>Zobacz też  
 [Projektant wstążki (MFC)](../mfc/ribbon-designer-mfc.md)

