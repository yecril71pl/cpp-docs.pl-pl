---
title: Dodawanie obiektów i kontrolek do projektu ATL
ms.date: 05/09/2019
f1_keywords:
- vc.appwiz.ATL.controls
helpviewer_keywords:
- ATL projects, adding objects
- wizards [C++], ATL projects
- ATL projects, adding controls
- controls [ATL], adding to projects
- objects [C++], adding to ATL projects
- ATL Control Wizard
ms.assetid: c0adcbd0-07fe-4c55-a8fd-8c2c65ecdaad
ms.openlocfilehash: 6acd60d430f13906d11e9a9b3e7c5655ee94badb
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499310"
---
# <a name="adding-objects-and-controls-to-an-atl-project"></a>Dodawanie obiektów i kontrolek do projektu ATL

> [!NOTE]
> Kreator składnika ATL COM+ 1,0, Kreator ATL OLE DB użytkownika i ATL Active Server Web Component nie są dostępne w programie Visual Studio 2019 lub nowszym.

Można użyć jednego z kreatorów kodu ATL, aby dodać obiekt lub formant do projektów opartych na ATL lub MFC. Dla każdego obiektu COM lub dodawanej kontrolki Kreator generuje pliki. cpp i. h, a także plik. RGS na potrzeby obsługi rejestru opartego na skrypcie. Następujące kreatory kodu ATL są dostępne w programie Visual Studio:

- [Prosty obiekt ATL](../../atl/reference/atl-simple-object-wizard.md)
- [Okno dialogowe ATL](../../atl/reference/atl-dialog-wizard.md)
- [Formant ATL](../../atl/reference/atl-control-wizard.md)
- [Strona właściwości ATL](../../atl/reference/atl-property-page-wizard.md)
- [Składnik strony Active Server ATL](../../atl/reference/atl-active-server-page-component-wizard.md)
- [Klient ATL OLE DB](../../atl/reference/atl-ole-db-consumer-wizard.md)
- [Dodawanie obsługi ATL do MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)
- [Kreator składników ATL COM+ 1.0](../../atl/reference/atl-com-plus-1-0-component-wizard.md)
- [Dostawca OLE DB ATL](../../atl/reference/atl-ole-db-provider-wizard.md)

> [!NOTE]
> Przed dodaniem obiektu ATL do projektu, należy przejrzeć szczegóły i wymagania dotyczące obiektu w powiązanych tematach pomocy.

## <a name="to-add-an-object-or-a-control-using-the-atl-control-wizard"></a>Aby dodać obiekt lub kontrolkę przy użyciu kreatora kontrolki ATL

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu, a następnie kliknij polecenie **Dodaj** z menu skrótów. Kliknij pozycję **Dodaj klasę**.

   Pojawi się okno dialogowe [Dodaj klasę](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) .

1. Po wybraniu folderu **ATL** w okienku **Kategorie** wybierz obiekt do wstawienia z okienka **Szablony** . Kliknij przycisk **Otwórz**. Zostanie wyświetlony Kreator kodu dla wybranego obiektu.

   > [!NOTE]
   > Jeśli chcesz dodać obiekt ATL do projektu MFC, musisz dodać obsługę ATL do istniejącego projektu. Można to zrobić, postępując zgodnie z instrukcjami w temacie [Dodawanie obsługi ATL do projektu MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md).

   Alternatywnie, Jeśli podjęto próbę dodania obiektu ATL do projektu MFC bez uprzedniego dodania obsługi ATL, program Visual Studio będzie monitował o określenie, czy do projektu ma zostać dodana obsługa ATL. Kliknij przycisk **tak** , aby dodać obsługę ATL do projektu i otworzyć wybranego kreatora ATL.

## <a name="see-also"></a>Zobacz też

[Kreator projektu ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Typy projektów C++ w programie Visual Studio](../../build/reference/visual-cpp-project-types.md)<br/>
[Podstawowe informacje o obiektach COM ATL](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Programowanie za pomocą kodu ATL i języka uruchomieniowego C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Domyślne konfiguracje projektu ATL](../../atl/reference/default-atl-project-configurations.md)
