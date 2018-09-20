---
title: Dodawanie obsługi ATL do projektu MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.adding.atl.mfc
dev_langs:
- C++
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc0d21202478a02980dbc94dc866b769c3c71a9b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429737"
---
# <a name="adding-atl-support-to-your-mfc-project"></a>Dodawanie obsługi ATL do projektu MFC

Jeśli utworzono już aplikacja oparta na MFC, następnie można dodać obsługę dla Active Template Library (ATL) łatwe, uruchamiając Dodaj ATL pomocy technicznej, aby Kreator projektu MFC.

> [!NOTE]
>  ATL i MFC nie są zazwyczaj obsługiwane w wersjach Express programu Visual Studio.

> [!NOTE]
>  Ta funkcja dotyczy tylko proste obiekty COM, dodane do projektu biblioteki DLL lub pliku wykonywalnego MFC. Możesz dodać inne obiekty COM (w tym formantów ActiveX) do projektów MFC, ale obiektów może nie działać zgodnie z oczekiwaniami.

### <a name="to-add-atl-support-to-your-mfc-project"></a>Aby dodać obsługę ATL do projektu MFC

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt, do którego chcesz dodać obsługę ATL.

1. W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.

1. Wybierz **Dodawanie obsługi ATL do projektu MFC** ikony.

    > [!NOTE]
    >  Ta ikona znajduje się w folderze ATL **kategorie** okienka.

1. Po wyświetleniu monitu kliknij **tak** do Dodaj obsługę ATL.

Aby uzyskać więcej informacji na temat jak dodawanie obsługi ATL zmienia kod projektu MFC, zobacz [szczegóły ATL obsługuje dodanej przez kreatora ATL](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md)

## <a name="see-also"></a>Zobacz też

[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Dodawanie funkcji członkowskiej](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Dodawanie zmiennej członkowskiej](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Zastępowanie funkcji wirtualnych](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Handler komunikatów MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Nawigacja w strukturze klas](../../ide/navigating-the-class-structure-visual-cpp.md)
