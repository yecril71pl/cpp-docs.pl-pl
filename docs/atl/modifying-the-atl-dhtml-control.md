---
title: Modyfikowanie formant ATL DHTML | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- HTML controls, modifying
- DHTML controls
- DHTML controls, modifying
ms.assetid: c053f35f-8629-4600-9595-721f5956777a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 74ed32c0322d23cd3da1d439dcc8d8eadb246c13
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="modifying-the-atl-dhtml-control"></a>Modyfikowanie formant ATL DHTML
Kreator formantu ATL zawiera kod startowy, możesz skompilować i uruchomić formantu i pozwala zobaczyć, jak te metody są zapisywane w plikach projektu i jak DHTML wywołuje kodu C++ formantu przy użyciu metod wysyłania. Możesz dodać dowolną metodę wysyłania do interfejsu. Następnie można wywołać metody w zasobie HTML.  
  
#### <a name="to-modify-the-atl-dhtml-control"></a>Aby zmodyfikować formant ATL DHTML  
  
1.  W widoku klas rozwiń węzeł projektu kontroli.  
  
     Należy zauważyć, że interfejs, który kończy się na "UI" ma jedną metodę `OnClick`. Interfejs, który nie kończy się "UI" nie ma żadnych metod.  
  
2.  Dodaj metodę o nazwie `MethodInvoked` do interfejsu nie kończy się "UI".  
  
     Ta metoda zostanie dodany do interfejsu, który jest używany w kontenerze kontroli interakcji kontenera, aby nie interfejsu używane przez DHTML do interakcji z formantem. Tylko kontenera można wywołać tej metody.  
  
3.  Znajdź metody poza zastąpić jej metodą zastępczą w pliku .cpp i Dodaj kod, aby wyświetlić okno komunikatu, na przykład:  
  
 [!code-cpp[NVC_ATL_COM#5](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_1.cpp)]  
  
4.  Dodaj inną metodę o nazwie `HelloHTML`, w tym momencie, dodaj go do interfejsu, który kończy się na "UI". Znajdź zastąpić jej metodą zastępczą poza `HelloHTML` metody w .cpp pliku i Dodaj kod, aby wyświetlić okno komunikatu, na przykład:  
  
 [!code-cpp[NVC_ATL_COM#6](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_2.cpp)]  
  
5.  Dodaj metodę trzeci `GoToURL`, interfejsu, który kończy się "UI". Zaimplementuj tę metodę, wywołując [IWebBrowser2::Navigate](https://msdn.microsoft.com/library/aa752133.aspx)w następujący sposób:  
  
 [!code-cpp[NVC_ATL_COM#7](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_3.cpp)]  
  
     Można użyć **IWebBrowser2** metody ponieważ ATL dostarcza wskaźnik do interfejsu dla Ciebie w pliku .h.  
  
 Następnie zmodyfikuj zasobu HTML do wywoływania metod, który został utworzony. Należy dodać trzy przyciski wywołania tych metod.  
  
#### <a name="to-modify-the-html-resource"></a>Aby zmodyfikować zasobu HTML  
  
1.  W Eksploratorze rozwiązań kliknij dwukrotnie plik htm, aby wyświetlić zasobu HTML.  
  
     Sprawdź, czy kod HTML, szczególnie wywołań do metod wysyłania zewnętrznego systemu Windows. Kod HTML wywołuje projektu `OnClick` — metoda i parametry wskazują treści formantu (`theBody`) i kolor można przypisać ("`red`"). Tekst następujący po wywołaniu metody jest etykiety, który jest wyświetlany na przycisku.  
  
2.  Dodaj inny `OnClick` metody, Zmień kolor. Na przykład:  
  
 ```  
 <br>  
 <br>  
 <BUTTON onclick='window.external.OnClick(theBody, "white");'>Refresh</BUTTON>  
 ```  
  
     Ta metoda tworzy przycisku, **Odśwież**, czy użytkownik może kliknąć, aby przywrócić oryginalne, białe tło formantu.  
  
3.  Dodaj wywołanie `HelloHTML` została utworzona. Na przykład:  
  
 ```  
 <br>  
 <br>  
 <BUTTON onclick='window.external.HelloHTML();'>HelloHTML</BUTTON>  
 ```  
  
     Ta metoda tworzy przycisku, **HelloHTML**, który użytkownik może kliknąć, aby wyświetlić `HelloHTML` okno komunikatu.  
  
 Teraz można tworzyć i [sprawdzić zmodyfikowane formant DHTML](../atl/testing-the-modified-atl-dhtml-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa dla DHTML](../atl/atl-support-for-dhtml-controls.md)

