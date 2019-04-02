---
title: Dodawanie punktów połączenia do obiektu
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], adding to ATL objects
- Implement Connection Point ATL wizard
ms.assetid: 843531be-4a36-4db0-9d54-e029b1a72a8b
ms.openlocfilehash: 7341e69852ed804122e0196b51d305f5af0c35b9
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772947"
---
# <a name="adding-connection-points-to-an-object"></a>Dodawanie punktów połączenia do obiektu

[ALT — samouczek](../atl/active-template-library-atl-tutorial.md) pokazuje, jak utworzyć formant z obsługą punktów połączenia, jak dodać zdarzenia i sposób implementacji punktu połączenia. ATL implementuje punkty połączenia z [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) klasy.

Aby zaimplementować punktu połączenia, dostępne są dwie opcje:

- Implementuje własne wychodzących źródła zdarzeń, dodając punkt połączenia do formantu lub obiektu.

- Ponowne użycie interfejsu punktu połączenia zdefiniowane w innej biblioteki typów.

W obu przypadkach kreator implementacji punktu połączenia używa biblioteki typów, aby wykonać swoją pracę.

### <a name="to-add-a-connection-point-to-a-control-or-object"></a>Aby dodać punkt połączenia do formantu lub obiektu

1. Zdefiniuj dispinterface w bloku biblioteki pliku .idl. Jeśli włączono obsługę punktów połączenia po utworzeniu kontrolki za pomocą Kreatora formantu biblioteki ATL, dispinterface już być utworzone. Jeśli nie włączono obsługę punktów połączenia po utworzeniu kontrolki, należy ręcznie dodać dispinterface w pliku .idl. Oto przykład dispinterface. Interfejsy wychodzące nie są wymagane jako interfejsach wysyłki, ale wiele języków skryptów, takich jak VBScript i JScript, wymagają, aby w tym przykładzie użyto dwóch dispinterfaces:

   [!code-cpp[NVC_ATL_Windowing#81](../atl/codesnippet/cpp/adding-connection-points-to-an-object_1.idl)]

   Wygeneruj identyfikator GUID za pomocą narzędzia uuidgen.exe albo guidgen.exe.

2. Dodaj dispinterface jako `[default,source]` interfejsu w klasie coclass dla obiektu w pliku .idl projektu. Ponownie, jeśli włączono obsługę punktów połączenia po utworzeniu kontrolki, Kreator kontrolki ATL utworzy `[default,source`] wpisu. Aby ręcznie dodać ten wpis, Dodaj wiersz pogrubioną czcionką:

   [!code-cpp[NVC_ATL_Windowing#82](../atl/codesnippet/cpp/adding-connection-points-to-an-object_2.idl)]

   Można znaleźć w pliku .idl w [OK](../overview/visual-cpp-samples.md) próbki ATL, na przykład.

3. Widok klas umożliwia dodawanie metod i właściwości interfejsu zdarzenia. Kliknij prawym przyciskiem myszy klasę w widoku klas, wskaż opcję **Dodaj** w menu skrótów, a następnie kliknij przycisk **Dodawanie punktów połączenia**.

4. W **interfejsy źródła** Kreator implementacji punktu połączenia, wybierz pole listy **projektu interfejsach**. Jeśli wybierzesz interfejsu dla kontrolki i naciśnij klawisz **OK**, należy:

   - Generowanie pliku nagłówka, za pomocą klasy proxy zdarzeń, która implementuje kod, który spowoduje, że połączenia wychodzące dla zdarzenia.

   - Dodawanie wpisu do mapy punktu połączenia.

   Zostanie również wyświetlona lista wszystkich bibliotek typów na komputerze. Należy używać tylko jednej z tych bibliotek typu do zdefiniowania punktu połączenia, jeśli chcesz zaimplementować dokładnie tego samego interfejsu wychodzącego w innej biblioteki typów.

### <a name="to-reuse-a-connection-point-interface-defined-in-another-type-library"></a>Aby ponownie użyć interfejsu punktu połączenia zdefiniowane w innej biblioteki typów

1. W widoku klas kliknij prawym przyciskiem myszy klasę, która implementuje **BEGIN_COM_MAP** makro, wskaż **Dodaj** w menu skrótów, a następnie kliknij przycisk **Dodawanie punktów połączenia**.

2. W Kreator implementacji punktu połączenia wybierz bibliotekę typów i interfejs w bibliotece typów, a następnie kliknij przycisk **Dodaj**.

3. Przeprowadź edycję pliku .idl celu:

   - Skopiuj dispinterface w pliku .idl dla obiektu, którego źródła zdarzeń jest używany.

   - Użyj **importlib** instrukcje dotyczące tej biblioteki typów.

## <a name="see-also"></a>Zobacz także

[Punkt połączenia](../atl/atl-connection-points.md)
