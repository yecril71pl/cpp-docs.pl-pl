---
title: Dodawanie prostego obiektu ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.classes.adding.atl
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding objects
- objects [ATL]
- ATL, simple objects
ms.assetid: 9c57d2ef-0447-4c84-8982-3304b8e49847
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3746e911b4931759baef4d0f4e4f9de77ea834b
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765599"
---
# <a name="adding-an-atl-simple-object"></a>Dodawanie prostego obiektu ATL

Aby dodać obiekt ATL (biblioteki Active Template Library) do projektu, projekt musi być utworzony jako aplikacji ATL lub aplikacji MFC, który zawiera obsługę ATL. Możesz użyć [Kreator projektów ATL](../../atl/reference/atl-project-wizard.md) do tworzenia aplikacji biblioteki ATL, lub [Dodaj obiekt ATL do Twojej aplikacji MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) do zaimplementowania Obsługa ALT dla aplikacji MFC.

Można zdefiniować interfejsów COM dla nowego obiektu ATL, kiedy należy najpierw utworzyć lub je dodać później przy użyciu [implementuj interfejs](../../ide/implement-interface-wizard.md) polecenia z menu skrótów w widoku klas.

### <a name="to-add-an-atl-simple-object-to-your-atl-com-project"></a>Aby dodać prosty obiekt ATL do projektu ATL COM

1. W obu **Eksploratora rozwiązań** lub [Widok klas](/visualstudio/ide/viewing-the-structure-of-code), kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać prosty obiekt ATL.

2. W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.

3. W [Dodaj klasę](../../ide/add-class-dialog-box.md) kliknij w okienku szablonów, w oknie dialogowym **prosty obiekt ATL**, a następnie kliknij przycisk **Otwórz** do wyświetlenia [proste Kreator obiektówATL](../../atl/reference/atl-simple-object-wizard.md).

4. Ustaw dodatkowe opcje projektu na [opcje](../../atl/reference/options-atl-simple-object-wizard.md) strony Kreator prostych obiektów ATL.

5. Kliknij przycisk **Zakończ** można dodać obiektu do projektu.

## <a name="see-also"></a>Zobacz też

[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)   
[Dodawanie nowego interfejsu w projekcie ATL](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)   
[Dodawanie punktów połączenia do obiektu](../../atl/adding-connection-points-to-an-object.md)   
[Dodawanie metody](../../ide/adding-a-method-visual-cpp.md)   
[Klasy MFC](../../mfc/reference/adding-an-mfc-class.md)   
[Dodawanie rodzajowej klasy C++](../../ide/adding-a-generic-cpp-class.md)

