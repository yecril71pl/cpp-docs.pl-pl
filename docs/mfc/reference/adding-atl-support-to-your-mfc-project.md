---
title: Dodawanie obsługi ATL do projektu MFC
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.adding.atl.mfc
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
ms.openlocfilehash: 05c4e8ba54d9a573b422f136c9e8cf69e48d1c9a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371681"
---
# <a name="adding-atl-support-to-your-mfc-project"></a>Dodawanie obsługi ATL do projektu MFC

Jeśli utworzono już aplikację opartą na MFC, można łatwo dodać obsługę aktywnej biblioteki szablonów (ATL) przy użyciu ide.

> [!NOTE]
> Ta obsługa dotyczy tylko prostych obiektów COM dodanych do projektu wykonywalnego lub DLL MFC. Można dodać inne obiekty COM (w tym formanty ActiveX) do projektów MFC, ale obiekty mogą nie działać zgodnie z oczekiwaniami.

::: moniker range=">=vs-2019"

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu.

1. W menu skrótów kliknij polecenie **Dodaj**, a następnie kliknij polecenie **Nowy element**.

1. Wybierz **pozycję ATL** w lewym okienku, a następnie wybierz pozycję **Obsługa atl** w środkowym okienku.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-add-atl-support-to-your-mfc-project"></a>Aby dodać obsługę ATL do projektu MFC

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu.

1. W menu skrótów kliknij polecenie **Dodaj**, a następnie kliknij polecenie **Dodaj klasę**.

1. Wybierz **pozycję ATL** w lewym okienku, a następnie wybierz pozycję **Dodaj obsługę ATL do projektu MFC** w środkowym okienku.

::: moniker-end

Aby uzyskać więcej informacji o tym, jak dodanie pomocy technicznej ATL zmienia kod projektu MFC, zobacz [Szczegóły obsługi ATL dodawane przez Kreatora ATL](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md)

## <a name="see-also"></a>Zobacz też

[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Dodawanie funkcji elementu członkowskiego](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Dodawanie zmiennej elementu członkowskiego](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Zastępowanie funkcji wirtualnej](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Program obsługi komunikatów MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Poruszanie się po strukturze klasy](../../ide/navigate-code-cpp.md)
