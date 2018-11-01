---
title: Dodawanie kontrolki ATL
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
ms.assetid: 10223e7e-fdb7-4163-80c6-44aeafa8e6ce
ms.openlocfilehash: 26667c2ad3bb2cedb42767fe42ff0ad358fa6d66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487688"
---
# <a name="adding-an-atl-control"></a>Dodawanie kontrolki ATL

Ten kreator umożliwia dodawanie obiektu interfejsu użytkownika do projektu, który obsługuje interfejsów dla wszystkich potencjalnych kontenerów. Aby obsługiwać te interfejsy, projekt musi być utworzony jako aplikacji ATL lub aplikacji MFC, który zawiera obsługę ATL. Możesz użyć [Kreator projektów ATL](../../atl/reference/atl-project-wizard.md) do tworzenia aplikacji biblioteki ATL, lub [Dodaj obiekt ATL do Twojej aplikacji MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) do zaimplementowania Obsługa ALT dla aplikacji MFC.

## <a name="to-add-an-atl-control-to-your-project"></a>Aby dodać kontrolki ATL do projektu

1. W obu **Eksploratora rozwiązań** lub [Widok klas](/visualstudio/ide/viewing-the-structure-of-code), kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać prosty obiekt ATL.

1. Kliknij przycisk **Dodaj** z menu skrótów, a następnie kliknij przycisk **Dodaj klasę**.

1. W [Dodaj klasę](../../ide/add-class-dialog-box.md) kliknij w okienku szablonów, w oknie dialogowym **kontrolka ATL**, a następnie kliknij przycisk **Dodaj** do wyświetlenia [Kreator kontrolki ATL](../../atl/reference/atl-control-wizard.md).

Za pomocą **Kreator kontrolki ATL**, można utworzyć jeden z trzech typów formantów:

- Kontrolki standardowej

- Kontrolek złożonych

- Kontrolki DHTML

Dodatkowo zmniejszyć rozmiar formantu i usuwanie interfejsów, które nie są używane przez większość kontenerów, wybierając **kontrolka minimalnego** na **opcje** strony kreatora.

## <a name="see-also"></a>Zobacz też

[Dodawanie funkcji do kontrolek złożonych](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[Podstawowe informacje na temat obiektów COM ATL](../../atl/fundamentals-of-atl-com-objects.md)
