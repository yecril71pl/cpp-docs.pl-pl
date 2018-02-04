---
title: Dodawanie klasy (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.classes.adding
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ac87368f2bd38c32425799103fa3999dd11b3298
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2018
---
# <a name="adding-a-class-visual-c"></a>Dodawanie klasy (Visual C++)
Aby dodać klasę w projekcie Visual C++ w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **klasy**. Spowoduje to otwarcie [Dodaj klasę — okno dialogowe](../ide/add-class-dialog-box.md) okno dialogowe.  
  
 Po dodaniu klasy, należy określić nazwę, która różni się od klasy, które już istnieją w MFC lub ATL. Jeśli określono nazwę, która już istnieje w bibliotece albo IDE zawiera komunikat o błędzie.  
  
 Jeśli projekt konwencji nazewnictwa wymaga użycia istniejącej nazwy, następnie wystarczy tylko zmienić w przypadku co najmniej jednej litery w nazwie ponieważ C++ jest rozróżniana wielkość liter. Na przykład chociaż nie można nadać nazwy klasy `CDocument`, można określić nazwę `cdocument`.  
  
## <a name="what-kind-of-class-do-you-want-to-add"></a>Jakiego rodzaju klasy chcesz dodać?  
 W **Dodaj klasę** okno dialogowe, po rozwinięciu **Visual C++** węzła w okienku po lewej stronie, wyświetlanych jest kilka grup zainstalowanych szablonów. Grupy zawierają **CLR**, **ATL**, **MFC**, i **C++**. Po wybraniu grupy w środkowym okienku zostanie wyświetlona lista dostępnych szablonów w tej grupie. Każdy szablon zawiera pliki i kod źródłowy, która jest wymagana dla klasy.  
  
 Aby wygenerować nową klasę, wybierz szablon w środkowym okienku, wpisz nazwę klasy w **nazwa** i kliknij **Dodaj**. Spowoduje to otwarcie **Kreator dodawania klasy** tak, aby określić opcje dla klasy.  
  
-   Aby uzyskać więcej informacji na temat tworzenia klas MFC, zobacz [klasy MFC](../mfc/reference/adding-an-mfc-class.md).  
  
-   Aby uzyskać więcej informacji na temat tworzenia klasy ATL zobacz [prosty obiekt ATL](../atl/reference/adding-an-atl-simple-object.md).  
  
> [!NOTE]
>  Szablon **Dodaj obsługę ATL do MFC** nie tworzy klasę, ale zamiast tego konfiguruje projektu do ATL. Aby uzyskać więcej informacji, zobacz [Obsługa ATL w projekcie MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).  
  
 Aby utworzyć klasę C++, która nie używa MFC i ATL, CLR, użyj **klasy C++** szablonu w **C++** grupy zainstalowanych szablonów. Aby uzyskać więcej informacji, zobacz [Dodawanie klasy ogólnej C++](../ide/adding-a-generic-cpp-class.md).  
  
 Dostępne są dwa rodzaje klas C++ bazującej na formularzu. Pierwsza z nich, [klasy CFormView](../mfc/reference/cformview-class.md) tworzy klasy MFC. Drugi tworzy klasę CLR formularzy systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie aplikacji MFC opartej na formularzach](../mfc/reference/creating-a-forms-based-mfc-application.md)   
 [Okno dialogowe Dodaj klasę](../ide/add-class-dialog-box.md)   
 [Tworzenie projektów pulpitu za pomocą kreatorów aplikacji](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Dodawanie funkcji z kreatorami kodów](../ide/adding-functionality-with-code-wizards-cpp.md)