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
ms.openlocfilehash: 95a93268ca76516c1b3f736c106518ae6d94cc27
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326819"
---
# <a name="adding-an-atl-simple-object"></a>Dodawanie prostego obiektu ATL

Aby dodać obiekt ATL (biblioteki Active Template Library) do projektu, projekt musi być utworzony jako aplikacji ATL lub aplikacji MFC, który zawiera obsługę ATL. Możesz użyć [Kreator projektów ATL](../../atl/reference/atl-project-wizard.md) do tworzenia aplikacji biblioteki ATL, lub [Dodaj obiekt ATL do Twojej aplikacji MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) do zaimplementowania Obsługa ALT dla aplikacji MFC.

Można zdefiniować interfejsów COM dla nowego obiektu ATL, kiedy należy najpierw utworzyć lub je dodać później przy użyciu [implementuj interfejs](../../ide/implement-interface-wizard.md) polecenia **Widok klas** menu skrótów.

## <a name="to-add-an-atl-simple-object-to-your-atl-com-project"></a>Aby dodać prosty obiekt ATL do projektu ATL COM

1. W obu **Eksploratora rozwiązań** lub [Widok klas](/visualstudio/ide/viewing-the-structure-of-code), kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać prosty obiekt ATL.

1. W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.

1. W [Dodaj klasę](../../ide/add-class-dialog-box.md) dialogowym **szablony** okienku kliknij **prosty obiekt ATL**, a następnie kliknij przycisk **Otwórz** do wyświetlenia [Kreator prostych obiektów ATL](../../atl/reference/atl-simple-object-wizard.md).

1. Ustaw dodatkowe opcje projektu na [opcje](../../atl/reference/options-atl-simple-object-wizard.md) strony **prosty obiekt ATL** kreatora.

1. Kliknij przycisk **Zakończ** można dodać obiektu do projektu.

## <a name="see-also"></a>Zobacz także

[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Dodawanie nowego interfejsu w projekcie ATL](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)<br/>
[Dodawanie punktów połączenia do obiektu](../../atl/adding-connection-points-to-an-object.md)<br/>
[Dodawanie metody](../../ide/adding-a-method-visual-cpp.md)<br/>
[MFC Class](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Dodawanie rodzajowej klasy C++](../../ide/adding-a-generic-cpp-class.md)
