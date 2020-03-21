---
title: Dodawanie składnika strony Active Server ATL
ms.date: 05/09/2019
ms.assetid: 7be2204c-6e58-4099-8892-001b848c8987
ms.openlocfilehash: a84eeb20f047097e3dbb3c7f3bb5f5a12b069bcb
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075297"
---
# <a name="adding-an-atl-active-server-page-component"></a>Dodawanie składnika strony Active Server ATL

::: moniker range="vs-2019"

Kreator składnika strony Active Server ATL nie jest dostępny w programie Visual Studio 2019 i nowszych.

::: moniker-end

::: moniker range="<=vs-2017"

Aby dodać obiekt Active Template Library (ATL) do projektu, projekt musi zostać utworzony jako aplikacja ATL COM lub jako aplikacja MFC, która zawiera obsługę ATL. Możesz użyć [Kreatora projektu ATL](../../atl/reference/atl-project-wizard.md) do utworzenia aplikacji ATL, możesz wybrać opcję **Dodaj obsługę ATL do MFC** z okna dialogowego [Dodaj klasę](../../ide/add-class-dialog-box.md) lub [dodać obiekt ATL do aplikacji MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) w celu zaimplementowania obsługi ATL dla aplikacji MFC.

Składniki stron Active Server są częścią architektury Internet Information Services, która udostępnia następujące zaawansowane funkcje Web Development:

- Możesz osadzić składniki ASP na stronach HTML, aby utworzyć dynamiczną, niezależną od przeglądarki zawartość.

- Strony ASP umożliwiają udostępnianie opartych na standardach połączeń baz danych.

- Możesz użyć funkcji obsługi błędów ASP dla aplikacji sieci Web.

## <a name="to-add-an-atl-active-server-pages-component-to-your-project"></a>Aby dodać składnik ATL Active Server Pages do projektu

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać składnik strony Active Server ATL.

1. W menu skrótów kliknij polecenie **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.

1. W oknie dialogowym [Dodawanie klasy](../../ide/add-class-dialog-box.md) w okienku **Szablony** kliknij pozycję **ATL Active Server Strona składnika**, a następnie kliknij przycisk **otwórz** , aby wyświetlić [Kreatora składnika strony Active Server ATL](../../atl/reference/atl-active-server-page-component-wizard.md).

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Dodawanie nowego interfejsu w projekcie ATL](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)<br/>
[Dodawanie punktów połączenia do obiektu](../../atl/adding-connection-points-to-an-object.md)<br/>
[Dodawanie metody](../../ide/adding-a-method-visual-cpp.md)<br/>
[Klasa MFC](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Dodawanie rodzajowej klasy C++](../../ide/adding-a-generic-cpp-class.md)
