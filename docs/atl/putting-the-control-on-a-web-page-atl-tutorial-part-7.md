---
title: Umieszczanie kontrolki na stronie sieci Web (ALT — samouczek, część 7) | Dokumentacja firmy Microsoft
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0cd4076ac34af6ee4b19687f401376265bf0e872
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="putting-the-control-on-a-web-page-atl-tutorial-part-7"></a>Umieszczanie kontrolki na stronie sieci Web (ALT — Samouczek, część 7)
Formant jest zakończone. Aby wyświetlić formantu pracy w rzeczywistych sytuacji, umieszcza je na stronie sieci Web. Plik HTML, który zawiera formant został utworzony podczas definiowania formantu. Otwórz plik PolyCtl.htm z **Eksploratora rozwiązań**, i zobaczysz formantu na stronie sieci Web.  
  
 W tym kroku zostanie skrypt strony sieci Web odpowiadanie na zdarzenia. Należy również zmodyfikować formantu, aby dowiedzieć się, że formant jest obsługi skryptów w programie Internet Explorer.  
  
## <a name="scripting-the-web-page"></a>Wykonywanie skryptów strony sieci Web  
 Formant nie wykonywać żadnych czynności jeszcze zmienia strony sieci Web odpowiadanie na zdarzenia, które można wysyłać.  
  
#### <a name="to-script-the-web-page"></a>Skrypt strony sieci Web  
  
1.  Otwórz PolyCtl.htm i wybierz widok HTML. Dodaj następujące wiersze w kodzie HTML. Powinny zostać dodane po `</OBJECT>` lecz przed `</BODY>`.  
  
 ```  
 
 <SCRIPT LANGUAGE="VBScript">  
 <!--  
    Sub PolyCtl_ClickIn(x, y)  
    PolyCtl.Sides = PolyCtl.Sides + 1  
    End Sub  
    Sub PolyCtl_ClickOut(x, y)  
    PolyCtl.Sides = PolyCtl.Sides - 1  
    End Sub  
 -->  
 </SCRIPT>  
 ```  
  
2.  Zapisz plik HTM.  
  
 Dodano niektóre kod VBScript, który pobiera właściwości strony z formantu i zwiększa liczbę stron o jeden po kliknięciu wewnątrz formantu. Jeśli klikniesz przycisk poza kontrolą można zmniejszyć liczbę stron o jeden.  
  
## <a name="indicating-that-the-control-is-safe-for-scripting"></a>Wskazuje, że kontrolka jest bezpieczne dla wykonywania skryptów  
 Można wyświetlić strony sieci Web za pomocą formantu w programie Internet Explorer lub więcej wygodnie, użyj widoku przeglądarki sieci Web wbudowanych w programie Visual C++. Aby wyświetlić formantu w widoku przeglądarki sieci Web, kliknij prawym przyciskiem myszy PolyCtl.htm, a następnie kliknij przycisk **Wyświetl w przeglądarce**.  
  
 Oparte na bieżące ustawienia zabezpieczeń programu Internet Explorer, może pojawić się okno dialogowe pola stwierdzający, że formant nie może być bezpiecznie skryptu i może potencjalnie uszkodzić Alert zabezpieczeń. Na przykład, jeśli formant, który będzie wyświetlany plik, ale również ma `Delete` metody usunięto plik byłoby bezpieczne Jeśli właśnie wyświetlane na stronie. Go może nie być bezpiecznie skryptu, jednak ponieważ ktoś może wywołać `Delete` metody.  
  
> [!IMPORTANT]
>  W tym samouczku można zmienić ustawienia zabezpieczeń w programie Internet Explorer, aby uruchomić formantów ActiveX, które nie są oznaczone jako bezpieczne. W Panelu sterowania kliknij **właściwości internetowe** i kliknij przycisk **zabezpieczeń** do Zmień odpowiednie ustawienia. Po ukończeniu tego samouczka, Zmień ustawienia zabezpieczeń do pierwotnego stanu.  
  
 Można programowo alertów programu Internet Explorer Aby nie trzeba wyświetlić okno dialogowe Alert zabezpieczeń dla tego konkretnego formantu. Można to zrobić z `IObjectSafety` interfejsu i ATL dostarcza implementację tego interfejsu w klasie [IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md). Aby dodać interfejs do formantu, dodać `IObjectSafetyImpl` do listy dziedziczonych klas i Dodaj wpis dla niego na mapie modelu COM.  
  
#### <a name="to-add-iobjectsafetyimpl-to-the-control"></a>Aby dodać IObjectSafetyImpl do formantu  
  
1.  Dodaj następujący wiersz na końcu listy dziedziczonych klas w PolyCtl.h i Dodaj przecinka do poprzedniego wiersza:  
  
 [!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]  
  
2.  Dodaj następujący wiersz na mapie modelu COM w PolyCtl.h:  
  
 [!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]  
  
## <a name="building-and-testing-the-control"></a>Tworzenie i testowanie formantu  
 Tworzenie formantu. Po zakończeniu kompilacji, otwórz PolyCtl.htm w przeglądarce widoku ponownie. Teraz, strony sieci Web powinna być wyświetlana bezpośrednio, bez okna dialogowego alertu bezpieczeństwa. Kliknij wewnątrz wielokąta; Liczba stron zwiększa się o jeden. Kliknij poza wielokąta w celu zmniejszenia liczby stron. Jeśli spróbujesz się zmniejszyć liczbę stron poniżej trzech, zobaczysz komunikat o błędzie, który zostanie ustawiona.  
  
 [Wróć do kroku 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)  
  
## <a name="next-steps"></a>Następne kroki  
 To jest zakończenie samouczka ATL. Dla łącza do dodatkowych informacji ATL — informacje, zobacz [ATL strony początkowej](../atl/active-template-library-atl-concepts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek](../atl/active-template-library-atl-tutorial.md)

