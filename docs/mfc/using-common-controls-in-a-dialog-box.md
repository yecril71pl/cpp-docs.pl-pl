---
title: "Używanie formantów wspólnych w oknie dialogowym | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- common controls [MFC], in dialog boxes
- dialog box controls [MFC], common controls
- Windows common controls [MFC], in dialog boxes
ms.assetid: 17713caf-09f8-484a-bf54-5f48bf09cce9
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 67a9c77e6a8e5721bca6e3741b4b337cfdb42393
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-common-controls-in-a-dialog-box"></a>Używanie formantów wspólnych w oknie dialogowym
Formanty standardowe systemu Windows mogą być używane w [okien dialogowych](../mfc/dialog-boxes.md), tworzyć widoki, widoki rekordów i inne okna na podstawie szablonu okna dialogowego. Poniższa procedura z drobnymi zmianami będzie działać również formularzy.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-use-a-common-control-in-a-dialog-box"></a>Aby użyć formantu wspólnego w oknie dialogowym  
  
1.  Formant na szablon okna dialogowego [za pomocą edytora okien dialogowych](../mfc/using-the-dialog-editor-to-add-controls.md).  
  
2.  Dodaj do klasy okien dialogowych zmiennej członkowskiej, która reprezentuje kontrolkę. W **Dodawanie zmiennej członkowskiej** okno dialogowe wyboru **zmienna sterująca** i upewnij się, że **kontroli** został wybrany do **kategorii**.  
  
3.  Jeśli ten formant wspólnej dostarcza dane wejściowe, aby program, należy zadeklarować dodatkowy element członkowski variable(s) klasy okna dialogowego do obsługi tych wartości wejściowe.  
  
    > [!NOTE]
    >  Można dodać te zmienne Członkowskie przy użyciu menu kontekstowego w widoku klas (zobacz [Dodawanie zmiennej elementu członkowskiego](../ide/adding-a-member-variable-visual-cpp.md)).  
  
4.  W [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) dla klasy okien dialogowych, ustaw początkowy warunki formant. Za pomocą zmiennej członkowskiej utworzony w poprzednim kroku, należy użyć funkcji członkowskich można ustawić wartości początkowej oraz inne ustawienia. Zobacz poniższe opisy kontrolek, aby uzyskać więcej informacji na temat ustawień.  
  
     Można również użyć [wymiana danych okna dialogowego](../mfc/dialog-data-exchange-and-validation.md) (DDX), aby zainicjować kontrolki w oknie dialogowym.  
  
5.  W programy obsługi formantów w oknie dialogowym należy użyć zmiennej członka do manipulowania formantu. Opisy następujących formantów, aby uzyskać szczegółowe informacje o metodach.  
  
    > [!NOTE]
    >  Zmiennej członkowskiej będą istnieć tylko tak długo, jak istnieje okno dialogowe samej siebie. Nie można zbadać kontroli dla wartości wejściowych po zamknięciu okna dialogowego. Aby pracować z wartości wejściowych z formantu wspólnego, Zastąp `OnOK` w klasy okien dialogowych. W przypadku zastąpienia zapytania kontroli dla wartości wejściowych i przechowywania tych wartości w zmiennych Członkowskich klasy okna dialogowego.  
  
    > [!NOTE]
    >  Wymiana danych okna dialogowego umożliwia również ustawić lub pobrać wartości z formantów w oknie dialogowym.  
  
## <a name="remarks"></a>Uwagi  
 Dodanie niektórych typowych formantów do okna dialogowego spowoduje, że okno dialogowe przestanie działać. Zapoznaj się [dodawanie formantów do okna dialogowego spowoduje, że okno dialogowe funkcja już](../windows/adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function.md) Aby uzyskać więcej informacji na temat obsługi tej sytuacji.  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić  
  
-   [Dodawanie formantów do okna dialogowego ręcznie zamiast z edytora okien dialogowych](../mfc/adding-controls-by-hand.md)  
  
-   [Pochodzić z jednego z standardowe formanty standardowe systemu Windows formantu](../mfc/deriving-controls-from-a-standard-control.md)  
  
-   [Użyj formantu wspólnego jako okna podrzędnego](../mfc/using-a-common-control-as-a-child-window.md)  
  
-   [Komunikaty powiadomień za pomocą formantu](../mfc/receiving-notification-from-common-controls.md)  
  
-   [Użyj wymiana danych okna dialogowego (DDX)](../mfc/dialog-data-exchange-and-validation.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie i używanie formantów](../mfc/making-and-using-controls.md)   
 [Kontrolki](../mfc/controls-mfc.md)

