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
ms.openlocfilehash: 1724dd3eb73b82e34c5cc2b0c1965d73e099a708
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440056"
---
# <a name="adding-a-new-interface-in-an-atl-project"></a>Dodawanie nowego interfejsu w projekcie ATL

Po dodaniu interfejsu do kontrolki lub obiekt, do tworzenia funkcji poza zastąpić jej metodą zastępczą dla poszczególnych metod interfejsu. W obiekcie lub kontrolki można dodawać tylko te interfejsy, które obecnie znaleziony w istniejącej biblioteki typów. Ponadto klasy, w którym można dodać interfejs musi implementować [BEGIN_COM_MAP](com-map-macros.md#begin_com_map) — makro lub, jeśli projekt jest przypisane, musi ono posiadać `coclass` atrybutu.

Można dodać nowy interfejs do formantu w jeden z dwóch sposobów: ręcznie lub za pomocą kreatorów kodu, w widoku klas.

## <a name="to-use-code-wizards-in-class-view-to-add-an-interface-to-an-existing-object-or-control"></a>Do użycia kreatorów kodu w widoku klas, aby dodać interfejs do istniejącego obiektu lub kontrolki

1. W [Widok klas](/visualstudio/ide/viewing-the-structure-of-code), kliknij prawym przyciskiem myszy nazwę klasy kontrolki. Na przykład Pełna kontrola lub złożonej kontrolki lub innej klasy formantu, który implementuje makro BEGIN_COM_MAP w pliku nagłówka.

1. W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **implementuj interfejs**.

1. Wybierz interfejsy do implementacji w [Kreator implementacji interfejsu](../../ide/implement-interface-wizard.md). Jeśli interfejs nie istnieje w dowolnym dostępne biblioteki typów, następnie należy go ręcznie dodać do pliku .idl.

## <a name="to-add-a-new-interface-manually"></a>Aby ręcznie dodać nowy interfejs

1. Dodaj definicję nowego interfejsu w pliku .idl.

1. Pochodzi z obiektu lub formantu z interfejsu.

1. Utwórz nową [com_interface_entry —](com-interface-entry-macros.md#com_interface_entry) interfejsu lub, jeśli projekt jest przypisane, Dodaj `coclass` atrybutu.

1. Implementować metody interfejsu.

## <a name="see-also"></a>Zobacz też

[Kreator projektu ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Typy projektów Visual C++](../../ide/visual-cpp-project-types.md)<br/>
[Tworzenie projektów wykorzystujących interfejs Pulpitu za pomocą kreatorów aplikacji](../../ide/creating-desktop-projects-by-using-application-wizards.md)<br/>
[Programowanie za pomocą kodu ATL i C Run-Time](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Podstawowe informacje na temat obiektów COM ATL](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Domyślne konfiguracje projektu ATL](../../atl/reference/default-atl-project-configurations.md)
