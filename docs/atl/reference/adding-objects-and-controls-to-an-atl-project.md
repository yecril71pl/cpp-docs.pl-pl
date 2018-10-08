---
title: Dodawanie obiektów i kontrolek do projektu ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.controls
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding objects
- wizards [C++], ATL projects
- ATL projects, adding controls
- controls [ATL], adding to projects
- objects [C++], adding to ATL projects
- ATL Control Wizard
ms.assetid: c0adcbd0-07fe-4c55-a8fd-8c2c65ecdaad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5758dff128cd213442ec3738967ccd78e20e75af
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861138"
---
# <a name="adding-objects-and-controls-to-an-atl-project"></a>Dodawanie obiektów i kontrolek do projektu ATL

Można użyć jednego z kreatorów kodu biblioteki ATL, można dodać obiektu lub formantu do swoich projektów ATL lub MFC oparte na. Do każdego obiektu COM lub kontrolki, możesz dodać, Kreator generuje .cpp i .h plików, a także pliku .rgs obsługi opartych na skryptach rejestru. Następujących kreatorów kodu biblioteki ATL są dostępne w programie Visual Studio:

||||
|-|-|-|
|[Prosty obiekt ATL](../../atl/reference/atl-simple-object-wizard.md)|[Okno dialogowe ATL](../../atl/reference/atl-dialog-wizard.md)|[Kontrolka ATL](../../atl/reference/atl-control-wizard.md)|
|[Strony właściwości ATL](../../atl/reference/atl-property-page-wizard.md)|[Składnika strony Active Server ATL](../../atl/reference/atl-active-server-page-component-wizard.md)|[Konsumenta ATL OLE DB](../../atl/reference/atl-ole-db-consumer-wizard.md)|
|[Dodaj obsługę ATL do MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)|[Kreator składników ATL COM+ 1.0](../../atl/reference/atl-com-plus-1-0-component-wizard.md)|[Dostawcy ATL OLE DB](../../atl/reference/atl-ole-db-provider-wizard.md)|

> [!NOTE]
> Przed dodaniem obiektu ATL do projektu, należy przejrzeć szczegóły i wymagania dotyczące obiektu w jego powiązane tematy Pomocy.

## <a name="to-add-an-object-or-a-control-using-the-atl-control-wizard"></a>Aby dodać obiekt lub kontrolki przy użyciu kreator kontrolki ATL

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i kliknij przycisk **Dodaj** z menu skrótów. Kliknij przycisk **Dodaj klasę**.

   [Dodaj klasę](../../ide/add-class-dialog-box.md) pojawi się okno dialogowe.

1. Za pomocą **ATL** folder wybrany w **kategorie** okienku, wybierz obiekt do wstawienia z **szablony** okienka. Kliknij przycisk **Otwórz**. Zostanie wyświetlony Kreator kod dla wybranego obiektu.

   > [!NOTE]
   > Jeśli chcesz dodać obiekt ATL do projektu MFC, należy dodać obsługę ATL do istniejącego projektu. Można to zrobić, postępując zgodnie z instrukcjami w [Dodawanie obsługi ATL do projektu MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md).

   Alternatywnie Jeśli spróbujesz dodać obiekt ATL do projektu MFC bez wcześniej Dodawanie obsługi ATL programu Visual Studio wyświetli monit o określenie, czy mają obsługi ATL dodanej do projektu. Kliknij przycisk **tak** Dodaj obsługę ATL do projektu i Otwórz kreatora ATL wybrane.

## <a name="see-also"></a>Zobacz też

[Kreator projektu ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Typy projektów Visual C++](../../ide/visual-cpp-project-types.md)<br/>
[Tworzenie projektów wykorzystujących interfejs Pulpitu za pomocą kreatorów aplikacji](../../ide/creating-desktop-projects-by-using-application-wizards.md)<br/>
[Podstawowe informacje na temat obiektów COM ATL](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Programowanie za pomocą kodu ATL i C Run-Time](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Domyślne konfiguracje projektu ATL](../../atl/reference/default-atl-project-configurations.md)
