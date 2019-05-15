---
title: Dodawanie składnika strony Active Server ATL
ms.date: 05/09/2019
ms.assetid: 7be2204c-6e58-4099-8892-001b848c8987
ms.openlocfilehash: b6c1d23efdff6885cc8ab900aaf552db39631e6e
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706929"
---
# <a name="adding-an-atl-active-server-page-component"></a>Dodawanie składnika strony Active Server ATL


::: moniker range="vs-2019"

Kreator składników ATL strony ASP nie jest dostępne w programie Visual Studio 2019 r i nowszych.

::: moniker-end

::: moniker range="<=vs-2017"

Aby dodać obiekt Active Template Library (ATL) do projektu, projekt musi być utworzony jako aplikacji ATL COM lub aplikacji MFC, który zawiera obsługę ATL. Możesz użyć [Kreator projektów ATL](../../atl/reference/atl-project-wizard.md) do tworzenia aplikacji biblioteki ATL, można wybrać **Dodawanie obsługi ATL do MFC** z [klasy okno dialogowe Dodawanie](../../ide/add-class-dialog-box.md) okno dialogowe, możesz także [Dodaj obiekt ATL do Twojej aplikacji MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) do zaimplementowania Obsługa ALT dla aplikacji MFC.

Active Server Pages składniki są częścią architekturę Internet Information Services, która oferuje następujące funkcje zaawansowane programowanie sieci Web:

- Możesz osadzić składniki ASP do stron HTML do tworzenia zawartości dynamicznej, niezależnie od przeglądarki.

- Strony ASP służy do zapewniania łączności oparte na standardach bazy danych.

- Dla aplikacji sieci Web, można użyć możliwości obsługi błędów ASP.

## <a name="to-add-an-atl-active-server-pages-component-to-your-project"></a>Aby dodać składnik ATL strony ASP do projektu

1. W **Eksploratora rozwiązań** kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać składnik ATL strony ASP.

1. W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.

1. W [Dodaj klasę](../../ide/add-class-dialog-box.md) dialogowym **szablony** okienku kliknij **składnik strony Active Server ATL**, a następnie kliknij przycisk **Otwórz** do wyświetlenia [Kreator składników stron Active Server ATL](../../atl/reference/atl-active-server-page-component-wizard.md).

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Dodawanie nowego interfejsu w projekcie ATL](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)<br/>
[Dodawanie punktów połączenia do obiektu](../../atl/adding-connection-points-to-an-object.md)<br/>
[Dodawanie metody](../../ide/adding-a-method-visual-cpp.md)<br/>
[MFC Class](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Dodawanie rodzajowej klasy C++](../../ide/adding-a-generic-cpp-class.md)
