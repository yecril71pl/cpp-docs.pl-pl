---
title: "Dodawanie punktów połączenia do obiektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- connection points [C++], adding to ATL objects
- Implement Connection Point ATL wizard
ms.assetid: 843531be-4a36-4db0-9d54-e029b1a72a8b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f63ec5bd9029302192e640e42a3d012df347219d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="adding-connection-points-to-an-object"></a>Dodawanie punktów połączenia do obiektu
[ALT — samouczek](../atl/active-template-library-atl-tutorial.md) pokazano tworzenie formantu z obsługą punkty połączenia, jak dodać zdarzenia i sposób zaimplementowania punktu połączenia. ATL implementuje punkty połączenia z [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) klasy.  
  
 Aby zaimplementować punktu połączenia, dostępne są dwie opcje:  
  
-   Implementuje własne wychodzących źródło zdarzenia przez dodanie punktu połączenia do formantu lub obiektu.  
  
-   Ponowne użycie interfejsu punktu połączenia zdefiniowane w innym biblioteki typów.  
  
 W obu przypadkach kreator implementacji punktu połączenia używa biblioteki typów, aby wykonać swoją pracę.  
  
### <a name="to-add-a-connection-point-to-a-control-or-object"></a>Aby dodać punkt połączenia do formantu lub obiektu  
  
1.  Zdefiniuj dispinterface w bloku biblioteki pliku .idl. Włączenie obsługi punkty połączenia podczas tworzenia kontrolki z Kreator formantu ATL dispinterface już być utworzone. Jeśli nie włączono obsługę punkty połączenia podczas tworzenia kontrolki, musisz ręcznie dodać dispinterface w pliku .idl. Oto przykład dispinterface. Interfejsy wychodzące nie są wymagane jako interfejsy wysyłania, ale wiele języków skryptów, takich jak VBScript i JScript, wymagają, aby w tym przykładzie użyto dwóch dispinterfaces:  
  
     [!code-cpp[NVC_ATL_Windowing#81](../atl/codesnippet/cpp/adding-connection-points-to-an-object_1.idl)]  
  
     Narzędzie uuidgen.exe albo guidgen.exe do generowania identyfikatora GUID.  
  
2.  Dodaj dispinterface jako `[default,source]` interfejsu w klasie coclass dla obiekt w pliku .idl projektu. Ponownie, jeśli jest włączona obsługa punktów połączenia, podczas tworzenia kontrolki, Kreator formantu ATL utworzy `[default,source`] wpis. Aby ręcznie dodać ten wpis, Dodaj wiersz pogrubione:  
  
     [!code-cpp[NVC_ATL_Windowing#82](../atl/codesnippet/cpp/adding-connection-points-to-an-object_2.idl)]  
  
     Znajduje się w pliku .idl w [OK](../visual-cpp-samples.md) próbki ATL przykład.  
  
3.  Widok klas umożliwia dodanie metody i właściwości do interfejsu zdarzenia. Kliknij prawym przyciskiem myszy klasę w widoku klas, wskaż pozycję **Dodaj** na pasku menu skrótów, a następnie kliknij **Dodaj punkt połączenia**.  
  
4.  W **interfejsy źródłowe** Kreator implementacji punktu połączenia, wybierz pole listy **interfejsy projektu**. Jeśli wybierzesz interfejs dla formantu i naciśnij klawisz **OK**, będzie:  
  
    -   Generowanie pliku nagłówka z klasy serwera proxy zdarzeń, która implementuje kod, aby ułatwić wychodzące dla zdarzenia.  
  
    -   Dodaj wpis w mapie punktu połączenia.  
  
     Zostanie również wyświetlona lista wszystkich bibliotek typów na komputerze. Należy używać tylko jednego z innych bibliotek typów do definiowania punkt połączenia, aby zaimplementować dokładnie tego samego interfejsu wychodzących w innym biblioteki typów.  
  
### <a name="to-reuse-a-connection-point-interface-defined-in-another-type-library"></a>Do ponownego użycia interfejsu punktu połączenia zdefiniowane w innym biblioteki typów  
  
1.  W widoku klas, kliknij prawym przyciskiem myszy klasę, która implementuje **BEGIN_COM_MAP** makra, wskaż **Dodaj** na pasku menu skrótów, a następnie kliknij **Dodaj punkt połączenia**.  
  
2.  W Kreator implementacji punktu połączenia wybierz bibliotekę typów i interfejs w bibliotece typów, a następnie kliknij przycisk **Dodaj**.  
  
3.  Przeprowadź edycję pliku .idl albo:  
  
    -   Skopiuj dispinterface z pliku .idl dla obiekt, którego źródłem zdarzenia jest używany.  
  
    -   Użyj **importlib** instrukcje dotyczące tej biblioteki typów.  
  
## <a name="see-also"></a>Zobacz też  
 [Punkt połączenia](../atl/atl-connection-points.md)

