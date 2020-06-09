---
title: Wstawianie formularza do projektu
ms.date: 11/04/2016
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
ms.openlocfilehash: 8e3162ac3917781920130bcbed23864eb90afa59
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618432"
---
# <a name="inserting-a-form-into-a-project"></a>Wstawianie formularza do projektu

Formularze zapewniają wygodny kontener dla kontrolek. Możesz łatwo wstawić formularz oparty na MFC do swojej aplikacji, o ile aplikacja obsługuje biblioteki MFC.

### <a name="to-insert-a-form-into-your-project"></a>Aby wstawić formularz do projektu

1. W obszarze Widok klasy wybierz projekt, do którego chcesz dodać formularz, a następnie kliknij prawym przyciskiem myszy.

1. W menu skrótów kliknij pozycję **Dodaj** , a następnie kliknij pozycję **Dodaj klasę**.

   Jeśli **nowy formularz** nie jest dostępny, projekt może opierać się na Active Template Library (ATL). Aby dodać formularz do projektu ATL, należy [określić niektóre ustawienia](../atl/reference/application-settings-atl-project-wizard.md) podczas pierwszego tworzenia projektu.

1. W folderze **MFC** kliknij pozycję **Klasa MFC**.

1. Za pomocą kreatora klas MFC, Utwórz nową klasę pochodną od [CFormView](reference/cformview-class.md).

Visual C++ dodaje formularz do aplikacji, otwierając go w edytorze okien dialogowych, aby można było rozpocząć dodawanie kontrolek i pracować nad jej ogólnym projektem.

Może być konieczne wykonanie następujących dodatkowych czynności (nie dotyczy aplikacji opartych na oknach dialogowych):

1. Przesłoń `OnUpdate` funkcję członkowską.

1. Zaimplementuj funkcję członkowską, aby przenieść dane z widoku do dokumentu.

1. Utwórz `OnPrint` funkcję członkowską.

## <a name="see-also"></a>Zobacz też

[Widoki formularzy](form-views-mfc.md)
