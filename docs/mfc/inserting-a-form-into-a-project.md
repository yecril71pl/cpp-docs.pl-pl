---
title: Wstawianie formularza do projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ba22c87ee601d66ccfb1092047e69be42d8163c3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50052759"
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

## <a name="see-also"></a>Zobacz też

[Widoki formularzy](../mfc/form-views-mfc.md)

