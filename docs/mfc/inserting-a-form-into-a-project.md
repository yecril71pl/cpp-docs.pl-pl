---
title: Wstawianie formularza do projektu
ms.date: 11/04/2016
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
ms.openlocfilehash: 2fa344f2d84b39be4ee36fd845edb82c14b6c519
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57286533"
---
# <a name="inserting-a-form-into-a-project"></a>Wstawianie formularza do projektu

Formularze zapewniają wygodny kontenera dla formantów. Formularz oparty na bibliotece MFC można łatwo wprowadzić w aplikacji, tak długo, jak aplikacja obsługuje biblioteki MFC.

### <a name="to-insert-a-form-into-your-project"></a>Aby wstawić formularza do projektu

1. W widoku klas wybierz projekt, do którego chcesz dodać formularz, a następnie kliknij prawym przyciskiem myszy.

1. W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodaj klasę**.

   Jeśli **nowy formularz** polecenie jest niedostępne, projektu mogą opierać się na Active Template Library (ATL). Aby dodać formularz do projektu ATL, musisz mieć [określić pewne ustawienia](../atl/reference/application-settings-atl-project-wizard.md) tworząc po raz pierwszy projekt.

1. Z **MFC** folderu, kliknij przycisk **klasy MFC**.

1. Przy użyciu Kreatora klas MFC, wprowadź nową klasę pochodną [CFormView](../mfc/reference/cformview-class.md).

Visual C++ dodaje formularz do aplikacji, otwierając go w edytorze okien dialogowych, aby rozpocząć dodawanie kontrolek i pracy z całego projektu.

Można wykonać następujące czynności dodatkowe (nie dotyczy oparta na oknach dialogowych aplikacji):

1. Zastąp `OnUpdate` funkcja elementu członkowskiego.

1. Zaimplementuj funkcję członkowską, aby przenieść dane z widoku do dokumentu.

1. Utwórz `OnPrint` funkcja elementu członkowskiego.

## <a name="see-also"></a>Zobacz także

[Widoki formularzy](../mfc/form-views-mfc.md)
