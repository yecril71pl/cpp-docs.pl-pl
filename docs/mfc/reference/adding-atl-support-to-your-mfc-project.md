---
title: Dodawanie obsługi ATL do projektu MFC
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.adding.atl.mfc
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
ms.openlocfilehash: fba79db013cd9f4cc62ba5826b53e5fa9b15c83a
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108416"
---
# <a name="adding-atl-support-to-your-mfc-project"></a>Dodawanie obsługi ATL do projektu MFC

Jeśli utworzono już aplikację opartą na MFC, możesz łatwo dodać obsługę Active Template Library (ATL) przy użyciu środowiska IDE.

> [!NOTE]
>  Ta obsługa dotyczy tylko prostych obiektów COM dodanych do pliku wykonywalnego MFC lub projektu DLL. Można dodać inne obiekty COM (w tym kontrolki ActiveX) do projektów MFC, ale obiekty mogą nie działać zgodnie z oczekiwaniami.

::: moniker range=">=vs-2019"

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł projektu.

1. W menu skrótów kliknij polecenie **Dodaj**, a następnie kliknij pozycję **nowy element**.

1. Wybierz **ATL** w lewym okienku, a następnie wybierz opcję **Obsługa ATL** w środkowym okienku.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-add-atl-support-to-your-mfc-project"></a>Aby dodać obsługę ATL do projektu MFC

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł projektu.

1. W menu skrótów kliknij polecenie **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.

1. W lewym okienku wybierz pozycję **ATL** , a następnie wybierz pozycję **Dodaj obsługę ATL do projektu MFC** w środkowym okienku.

::: moniker-end

Aby uzyskać więcej informacji o tym, jak dodawanie obsługi ATL zmienia kod projektu MFC, zobacz [szczegóły obsługi ATL dodanej przez kreatora ATL](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md)

## <a name="see-also"></a>Zobacz także

[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Dodawanie funkcji członkowskiej](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Dodawanie zmiennej członkowskiej](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Zastępowanie funkcji wirtualnej](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Procedura obsługi komunikatów MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Nawigacja w strukturze klas](../../ide/navigate-code-cpp.md)
