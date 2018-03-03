---
title: "Dodawanie kontrolki (ALT — samouczek, część 2) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aed69a5dd421e967e1da33bb3a2f2c41fa80698d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="adding-a-control-atl-tutorial-part-2"></a>Dodawanie kontrolki (ALT — Samouczek, część 2)
W tym kroku zostanie Dodawanie formantu do projektu, skompiluj go i przetestować go na stronie sieci Web.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-add-an-object-to-an-atl-project"></a>Można dodać obiektu do Projekt ATL  
  
1.  W widoku klas kliknij prawym przyciskiem myszy projekt wielokąta.  
  
2.  Wskaż **Dodaj** na pasku menu skrótów, a następnie kliknij **klasy** w podmenu.  
  
     **Dodaj klasę** zostanie wyświetlone okno dialogowe. Kategorie różne obiekty są wyświetlane w strukturze drzewa po lewej stronie.  
  
3.  Kliknij przycisk **ATL** folderu.  
  
4.  Na liście szablonów po prawej stronie zaznacz **formantu ATL**. Kliknij przycisk **Dodaj**. Zostanie otwarty Kreator formantu ATL i sterowanie można skonfigurować.  
  
5.  Typ `PolyCtl` jako krótka nazwa i należy pamiętać, że inne pola zostały automatycznie zakończone. Nie klikaj pozycji **Zakończ** jeszcze, ponieważ trzeba wprowadzić kilka zmian.  
  
 Kreator formantu ATL **nazwy** strona zawiera następujące pola:  
  
|Pole|Spis treści|  
|-----------|--------------|  
|**Krótka nazwa**|Nazwa wprowadzona dla formantu.|  
|**Klasy**|Nazwa klasy C++ utworzone w celu wdrożenia formantu.|  
|**w pliku .h**|Plik zawiera definicję klasy C++.|  
|**plik .cpp**|Plik zawiera implementację klasy C++.|  
|**Klasa coClass**|Nazwa klasy składnika dla tego formantu.|  
|**Interfejs**|Nazwa interfejsu, na którym formantu zostanie Implementowanie niestandardowych metod i właściwości.|  
|**Typ**|Opis dla formantu.|  
|**Identyfikator programu**|Dla użytkownika nazwę używaną do odszukania CLSID formantu.|  
  
 Konieczne będzie wprowadzenie kilka dodatkowych ustawień kreatora ATL kontroli.  
  
#### <a name="to-enable-support-for-rich-error-information-and-connection-points"></a>Aby włączyć obsługę połączenia i informacje o błędzie sformatowanego punkty  
  
1.  Kliknij przycisk **opcje** otworzyć **opcje** strony.  
  
2.  Wybierz **punkty połączenia** pole wyboru. Spowoduje to utworzenie obsługę interfejsu wychodzącego w pliku IDL.  
  
 Należy również wybrać formant insertable, co oznacza, że można ją osadzić w aplikacji, które obsługuje osadzonych obiektów, takich jak Excel lub Word.  
  
#### <a name="to-make-the-control-insertable"></a>Aby insertable formantu  
  
1.  Kliknij przycisk **wygląd** otworzyć **wygląd** strony.  
  
2.  Wybierz **Insertable** pole wyboru.  
  
 Wielokąt wyświetlany przez obiekt będzie mieć kolor wypełnienia stałe, dlatego należy dodać `Fill Color` podstawowy właściwości.  
  
#### <a name="to-add-a-fill-color-stock-property-and-create-the-control"></a>Dodawanie właściwości standardowych kolor wypełnienia i utworzyć formantu  
  
1.  Kliknij przycisk **właściwości zasobów** otworzyć **właściwości zasobu** strony.  
  
2.  W obszarze **nieobsługiwane**, przewiń w dół listę możliwych właściwości standardowych. Kliknij dwukrotnie `Fill Color` docelowy **obsługiwane** listy.  
  
3.  Na tym kończy się opcji dla formantu. Kliknij przycisk **Zakończ**.  
  
 Kreator tworzenia kontrolki, wystąpił kilka zmian w kodzie i pliku dodatków. Następujące pliki zostały utworzone:  
  
|Plik|Opis|  
|----------|-----------------|  
|PolyCtl.h|Zawiera większość Implementacja klasy C++ `CPolyCtl`.|  
|PolyCtl.cpp|Pozostałe części zawiera `CPolyCtl`.|  
|PolyCtl.rgs|Plik tekstowy zawierający skrypt rejestru używany do rejestrowania formantu.|  
|PolyCtl.htm|Strony sieci Web zawierającej odwołanie do nowo utworzonej formantu.|  
  
 Kreator również wykonać następujące zmiany kodu:  
  
-   Dodaje `#include` instrukcji do pliku stdafx.h i stdafx.cpp w celu ATL pliki niezbędne do obsługi formantów.  
  
-   Zmienione Polygon.idl uwzględnienie szczegółów nowego formantu.  
  
-   Dodany nowy formant do mapy obiektu w Polygon.cpp.  
  
 Teraz można tworzyć formant jest widoczny w akcji.  
  
## <a name="building-and-testing-the-control"></a>Tworzenie i testowanie formantu  
  
#### <a name="to-build-and-test-the-control"></a>Tworzenie i testowanie formantu  
  
1.  Na **kompilacji** menu, kliknij przycisk **kompilacji wielokąta**.  
  
     Gdy formant kończy budynku, kliknij prawym przyciskiem myszy PolyCtl.htm w **Eksploratora rozwiązań** i wybierz **Wyświetl w przeglądarce**. Wyświetli się strona sieci HTML Web zawierająca formant. Powinna zostać wyświetlona strona z tytułem "ATL strony testowej 8.0 dla obiekt PolyCtl" i tekst **PolyCtl**. To jest formant.  
  
> [!NOTE]
>  Po ukończeniu tego samouczka, jeśli zostanie wyświetlony komunikat o błędzie, której nie można utworzyć pliku biblioteki DLL, zamknij plik PolyCtl.htm i kontener testu formantu ActiveX i ponownie skompiluj rozwiązanie. Jeśli nadal nie można utworzyć biblioteki DLL, ponownego uruchamiania komputera lub wylogowywanie (Jeśli używasz usług terminalowych).  
  
 Następnie dodasz właściwości niestandardowych do formantu.  
  
 [Wróć do kroku 1](../atl/creating-the-project-atl-tutorial-part-1.md) &#124; [Do kroku 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek](../atl/active-template-library-atl-tutorial.md)

