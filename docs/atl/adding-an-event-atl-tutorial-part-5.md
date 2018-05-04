---
title: Dodawanie zdarzenia (ALT — samouczek, część 5) | Dokumentacja firmy Microsoft
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 2de12022-3148-4ce3-8606-8a9d4274f0e9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a118cf29546ac8dae2e882d5658b07e3b5e085f6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="adding-an-event-atl-tutorial-part-5"></a>Dodawanie zdarzenia (ALT — Samouczek, część 5)
W tym kroku zostaną dodane `ClickIn` i `ClickOut` zdarzenia do formantu ATL. Zostanie zastosowana `ClickIn` zdarzeń, gdy użytkownik kliknie w wielokąta i fire `ClickOut` gdy użytkownik kliknie poza. Dostępne są następujące zadania, aby dodać zdarzenie:  
  
-   Dodawanie `ClickIn` i `ClickOut` metody  
  
-   Generowanie biblioteki typów  
  
-   Implementowanie interfejsów punktu połączenia  
  
## <a name="adding-the-clickin-and-clickout-methods"></a>Dodawanie clickin — i metody ClickOut  
 Po utworzeniu formantu ATL w kroku 2 wybrano **punkty połączenia** pole wyboru. To utworzony `_IPolyCtlEvents` interfejsu w pliku Polygon.idl. Należy pamiętać, że nazwa interfejsu, który rozpoczyna się od znaku podkreślenia. Jest to Konwencji, aby wskazać, że interfejs jest interfejsem wewnętrznym. W związku z tym programy, które umożliwiają przeglądanie obiektów COM można nie wyświetlać interfejsu użytkownika. Należy również zauważyć, że zaznaczenie **punkty połączenia** Dodaj poniższy wiersz w pliku Polygon.idl, aby wskazać, że `_IPolyCtlEvents` jest domyślny interfejs źródłowy:  
  
 `[default, source] dispinterface _IPolyCtlEvents;`  
  
 Atrybut źródłowy wskazuje, czy kontrolka jest źródła powiadomień, więc ten interfejs zostanie wywołany w kontenerze.  
  
 Teraz Dodaj `ClickIn` i `ClickOut` metody `_IPolyCtlEvents` interfejsu.  
  
#### <a name="to-add-the-clickin-and-clickout-methods"></a>Aby dodać metody clickin — i ClickOut  
  
1.  W widoku klas rozwiń wielokątów i PolygonLib, aby wyświetlić _IPolyCtlEvents.  
  
2.  Kliknij prawym przyciskiem myszy _IPolyCtlEvents. W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj metodę**.  
  
3.  Wybierz **zwracany typ** z `void`.  
  
4.  Wprowadź `ClickIn` w **nazwę metody** pole.  
  
5.  W obszarze **atrybuty parametru**, wybierz pozycję **w** pole.  
  
6.  Wybierz **typ parametru** z `LONG`.  
  
7.  Typ `x` jako **Nazwa parametru**i kliknij przycisk **Dodaj**.  
  
8.  Powtórz kroki od 5 do 7, tym razem dla **Nazwa parametru** z `y`.  
  
9. Kliknij przycisk **Dalej**.  
  
10. Typ `method ClickIn` jako **HelpString —**.  
  
11. Kliknij przycisk **Zakończ**.  
  
12. Powtórz powyższe kroki, aby zdefiniować `ClickOut` metody o tej samej `LONG` parametry `x` i `y`, taki sam **atrybuty parametru** i tym samym `void` typ zwracany.  
  
 Sprawdź plik Polygon.idl, aby zobaczyć, czy kod został dodany do `_IPolyCtlEvents` dispinterface.  
  
 `_IPolyCtlEvents` Dispinterface w pliku Polygon.idl powinna wyglądać następująco:  
  
 [!code-cpp[NVC_ATL_Windowing#56](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_1.idl)]  
  
 `ClickIn` i `ClickOut` metody podjęcie x i y współrzędne punktu klikniętego jako parametry.  
  
## <a name="generating-the-type-library"></a>Generowanie biblioteki typów  
 Generuj bibliotekę typów w tym momencie, ponieważ kreatora punktu połączenia użyje on tego aby uzyskać informacje potrzebne do utworzenia punktu połączenia i interfejsem kontener punktu połączenia dla formantu.  
  
#### <a name="to-generate-the-type-library"></a>Aby wygenerować biblioteki typów  
  
1.  Ponownie skompiluj projekt.  
  
     —lub—  
  
2.  Kliknij prawym przyciskiem myszy plik Polygon.idl w Eksploratorze rozwiązań i kliknij przycisk **skompilować** menu skrótów.  
  
 Spowoduje to utworzenie pliku Polygon.tlb, który jest biblioteki typów. Plik Polygon.tlb nie jest widoczny w Eksploratorze rozwiązań, ponieważ jego jest to plik binarny i nie można wyświetlić lub edytować bezpośrednio.  
  
## <a name="implementing-the-connection-point-interfaces"></a>Implementowanie interfejsów punktu połączenia  
 Implementowanie interfejsu punktu połączenia oraz interfejs kontener punktu połączenia dla formantu. W modelu COM zdarzenia są implementowane za pośrednictwem mechanizmu punkty połączenia. Na odbieranie zdarzeń z obiektu COM, kontener ustanawia połączenie zespół doradczy do punktu połączenia, który implementuje obiektu COM. Ponieważ obiekt COM może mieć wiele punktów połączenia, obiektu COM również implementuje interfejs kontener punktu połączenia. Za pośrednictwem tego interfejsu kontenera można określić, które punktów połączenia są obsługiwane.  
  
 Interfejs, który implementuje punkt połączenia jest nazywany `IConnectionPoint`, i nosi nazwę interfejsu, który implementuje kontener punktu połączenia `IConnectionPointContainer`.  
  
 Aby zaimplementować `IConnectionPoint`, użyje Kreator implementacji punktu połączenia. Ten kreator generuje `IConnectionPoint` interfejsu odczytu biblioteki typów i wdrożenie funkcją dla każdego zdarzenia, które mogą być uruchamiane.  
  
#### <a name="to-use-the-implement-connection-point-wizard"></a>Aby użyć Kreator implementacji punktu połączenia  
  
1.  W widoku klas, kliknij prawym przyciskiem myszy klasa implementacji formantu `CPolyCtl`.  
  
2.  W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj punkt połączenia**.  
  
3.  Wybierz `_IPolyCtlEvents` z **interfejsy źródłowe** listy i kliknij dwukrotnie, aby dodać go do **zaimplementować punkty połączenia** kolumny. Kliknij przycisk **Zakończ**. Klasy serwera proxy punktu połączenia zostanie wygenerowany, w tym przypadku `CProxy_IPolyCtlEvents`.  
  
 Jeśli przyjrzymy się _IPolyCtlEvents_CP.h wygenerowany plik w Eksploratorze rozwiązań, zobaczysz, czy ma ona klasy o nazwie `CProxy_IPolyCtlEvents` która pochodzi z `IConnectionPointImpl`. _IPolyCtlEvents_CP.h definiuje również dwie metody `Fire_ClickIn` i `Fire_ClickOut`, które mają po dwa parametry współrzędnych. Tych metod można wywołać, gdy chcesz zdarzenia z formantu.  
  
 Kreator również został dodany `CProxy_PolyEvents` i `IConnectionPointContainerImpl` do wielu listy dziedziczenia spod kontroli. Kreator również widoczne `IConnectionPointContainer` dla Ciebie, dodając odpowiednie wpisy na mapie modelu COM.  
  
 Po zakończeniu wdrażania kodu do obsługi zdarzeń. Teraz Dodaj kod do uruchamiania zdarzeń w odpowiedniej chwili. Należy pamiętać, że będą wyzwalać `ClickIn` lub `ClickOut` zdarzenie, gdy użytkownik kliknie lewego przycisku myszy w formancie. Aby dowiedzieć się, gdy użytkownik kliknie przycisk, Dodaj program obsługi `WM_LBUTTONDOWN` wiadomości.  
  
#### <a name="to-add-a-handler-for-the-wmlbuttondown-message"></a>Aby dodać obsługę wiadomości WM_LBUTTONDOWN  
  
1.  W widoku klas, kliknij prawym przyciskiem myszy klasę CPolyCtl, a następnie kliknij przycisk **właściwości** menu skrótów.  
  
2.  W **właściwości** okna, kliknij przycisk **wiadomości** ikonę, a następnie kliknij przycisk `WM_LBUTTONDOWN` na liście z lewej strony.  
  
3.  Z listy rozwijanej, która jest wyświetlana, kliknij przycisk  **\<Dodaj > OnLButtonDown**. `OnLButtonDown` Deklaracja obsługi zostaną dodane do PolyCtl.h i implementację programu obsługi, które zostaną dodane do PolyCtl.cpp.  
  
 Następnie zmodyfikuj program obsługi.  
  
#### <a name="to-modify-the-onlbuttondown-method"></a>Aby zmodyfikować OnLButtonDown — metoda  
  
1.  Zmień kod, który obejmuje `OnLButtonDown` metody w PolyCtl.cpp (dowolny kod umieszczony w Kreatorze usuwania), aby wygląda następująco:  
  
     [!code-cpp[NVC_ATL_Windowing#57](../atl/codesnippet/cpp/adding-an-event-atl-tutorial-part-5_2.cpp)]  
  
 Ten kod sprawia, że korzystanie z punktów jest obliczane w `OnDraw` funkcji, aby utworzyć region, który wykryje użytkownika kliknięcia myszą przez wywołanie do `PtInRegion`.  
  
 `uMsg` Parametr jest identyfikator komunikatu systemu Windows są obsługiwane. Dzięki temu można mieć jedną funkcję, która obsługuje szeroką gamę wiadomości. `wParam` i `lParam` parametry są standardowymi wartościami wiadomości są obsługiwane. BHandled parametr umożliwia określenie, czy funkcja obsługi wiadomości. Domyślnie ta wartość jest równa `TRUE` aby wskazać, że funkcji obsługi wiadomości, ale można ją ustawić `FALSE`. Spowoduje to ALT kontynuować wyszukiwanie innej funkcji obsługi komunikatów do wysłania tej wiadomości do.  
  
## <a name="building-and-testing-the-control"></a>Tworzenie i testowanie formantu  
 Wypróbuj teraz zdarzeń. Tworzenie formantu, a następnie ponownie uruchom kontener testu formantu ActiveX. Teraz, Wyświetl okno Dziennik zdarzeń. Aby rozesłać zdarzeń w oknie danych wyjściowych, kliknij przycisk **rejestrowanie** z **opcje** menu i wybierz **dziennika w oknie danych wyjściowych**. Wstawianie formantu i spróbuj kliknąć w oknie. Należy pamiętać, że `ClickIn` jest wywoływane po kliknięciu w wypełniony wielokąt i `ClickOut` jest wywoływane po kliknięciu poza programem.  
  
 Następnie można dodać strony właściwości.  
  
 [Wróć do kroku 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md) &#124; [do kroku 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek](../atl/active-template-library-atl-tutorial.md)

