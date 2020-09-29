---
title: Dodawanie prostego obiektu ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.adding.atl
helpviewer_keywords:
- ATL projects, adding objects
- objects [ATL]
- ATL, simple objects
ms.assetid: 9c57d2ef-0447-4c84-8982-3304b8e49847
ms.openlocfilehash: 85c19c483ff27bd34431ec163e3baadac1855236
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499339"
---
# <a name="adding-an-atl-simple-object"></a>Dodawanie prostego obiektu ATL

Aby dodać obiekt ATL (Active Template Library) do projektu, projekt musi zostać utworzony jako aplikacja ATL lub aplikacja MFC, która zawiera obsługę ATL. Możesz użyć [Kreatora projektu ATL](../../atl/reference/atl-project-wizard.md) do utworzenia aplikacji ATL lub [dodać obiekt ATL do aplikacji MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) w celu zaimplementowania obsługi ATL dla aplikacji MFC.

Można zdefiniować interfejsy COM dla nowego obiektu ATL podczas jego pierwszego tworzenia lub dodać je później przy użyciu polecenia [Implementuj interfejs](../../ide/implementing-an-interface-visual-cpp.md#implement-interface-wizard) z menu skrótów **Widok klasy** .

## <a name="to-add-an-atl-simple-object-to-your-atl-com-project"></a>Aby dodać prosty obiekt ATL do projektu ATL COM

1. W **Eksplorator rozwiązań** lub [Widok klasy](/visualstudio/ide/viewing-the-structure-of-code), kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać prosty obiekt ATL.

1. W menu skrótów kliknij polecenie **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.

1. W oknie dialogowym [Dodaj klasę](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) , w okienku **Szablony** kliknij pozycję **ATL Simple Object**, a następnie kliknij przycisk **Otwórz** , aby wyświetlić [Kreatora prostych obiektów ATL](../../atl/reference/atl-simple-object-wizard.md).

1. Ustaw dodatkowe opcje dla projektu na stronie [Opcje](../../atl/reference/options-atl-simple-object-wizard.md) kreatora **prostych obiektów ATL** .

1. Kliknij przycisk **Zakończ** , aby dodać obiekt do projektu.

## <a name="see-also"></a>Zobacz też

[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Dodawanie nowego interfejsu w projekcie ATL](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)<br/>
[Dodawanie punktów połączenia do obiektu](../../atl/adding-connection-points-to-an-object.md)<br/>
[Dodawanie metody](../../ide/adding-a-method-visual-cpp.md)<br/>
[Klasa MFC](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Dodawanie rodzajowej klasy C++](../../ide/adding-a-generic-cpp-class.md)
