---
title: Dodawanie nowego interfejsu w projekcie ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.interface
helpviewer_keywords:
- interfaces, adding to ATL objects
- Implement Interface ATL wizard
- controls [ATL], interfaces
- ATL projects, adding interfaces
ms.assetid: 7d34b023-2c6b-4155-aca3-d47a40968063
ms.openlocfilehash: 8bf0138f85929e06b67e9a2e294eda8a2f385e1a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499379"
---
# <a name="adding-a-new-interface-in-an-atl-project"></a>Dodawanie nowego interfejsu w projekcie ATL

Po dodaniu interfejsu do obiektu lub kontrolki, tworzysz użyto metod zastępczych funkcje dla każdej metody w tym interfejsie. W obiekcie lub formancie można dodawać tylko interfejsy znajdujące się obecnie w istniejącej bibliotece typów. Ponadto Klasa, w której został dodany interfejs, musi implementować [BEGIN_COM_MAP](com-map-macros.md#begin_com_map) makro lub, jeśli projekt jest przypisany, musi mieć `coclass` atrybut.

Nowy interfejs można dodać do formantu na jeden z dwóch sposobów: ręcznie lub za pomocą kreatorów kodu w Widok klasy.

## <a name="to-use-code-wizards-in-class-view-to-add-an-interface-to-an-existing-object-or-control"></a>Aby użyć kreatorów kodu w Widok klasy, aby dodać interfejs do istniejącego obiektu lub kontrolki

1. W [Widok klasy](/visualstudio/ide/viewing-the-structure-of-code)kliknij prawym przyciskiem myszy nazwę klasy kontrolki. Na przykład Pełna kontrola lub złożona kontrolka lub jakakolwiek inna Klasa formantów, która implementuje makro BEGIN_COM_MAP w pliku nagłówkowym.

1. W menu skrótów kliknij pozycję **Dodaj**, a następnie kliknij pozycję **Implementuj interfejs**.

1. Wybierz interfejsy do zaimplementowania w [Kreatorze implementacji interfejsu](../../ide/implementing-an-interface-visual-cpp.md#implement-interface-wizard). Jeśli interfejs nie istnieje w żadnej z dostępnych typów TypeLib, należy dodać go ręcznie do pliku. idl.

## <a name="to-add-a-new-interface-manually"></a>Aby ręcznie dodać nowy interfejs

1. Dodaj definicję nowego interfejsu do pliku IDL.

1. Utwórz obiekt lub kontrolkę z interfejsu.

1. Utwórz nowy [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) dla interfejsu lub, jeśli atrybut jest przypisany do projektu, Dodaj `coclass` atrybut.

1. Implementuj metody w interfejsie.

## <a name="see-also"></a>Zobacz też

[Kreator projektu ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Typy projektów C++ w programie Visual Studio](../../build/reference/visual-cpp-project-types.md)<br/>
[Programowanie za pomocą kodu ATL i języka uruchomieniowego C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Podstawowe informacje o obiektach COM ATL](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Domyślne konfiguracje projektu ATL](../../atl/reference/default-atl-project-configurations.md)
