---
title: Używanie formantów wspólnych w oknie dialogowym
ms.date: 11/04/2016
helpviewer_keywords:
- common controls [MFC], in dialog boxes
- dialog box controls [MFC], common controls
- Windows common controls [MFC], in dialog boxes
ms.assetid: 17713caf-09f8-484a-bf54-5f48bf09cce9
ms.openlocfilehash: 1a3dcb7151952b52affcfeb838ced15f0d116fce
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500348"
---
# <a name="using-common-controls-in-a-dialog-box"></a>Używanie formantów wspólnych w oknie dialogowym

Formantów wspólnych systemu Windows można używać w [oknach dialogowych](../mfc/dialog-boxes.md), widokach formularzy, widokach rekordów i innych oknach opartych na szablonie okna dialogowego. Poniższa procedura z drobnymi zmianami również będzie działała dla formularzy.

## <a name="procedures"></a>Procedury

#### <a name="to-use-a-common-control-in-a-dialog-box"></a>Aby użyć kontrolki typowej w oknie dialogowym

1. Umieść formant w szablonie okna dialogowego [przy użyciu edytora okien dialogowych](../mfc/using-the-dialog-editor-to-add-controls.md).

1. Dodaj do klasy okna dialogowego, która reprezentuje kontrolkę. W oknie dialogowym **Dodaj zmienną członkowską** Sprawdź pozycję **zmienna kontroli** i upewnij się, że wybrano pozycję **Kontrola** dla **kategorii**.

1. Jeśli ten wspólny formant dostarcza dane wejściowe do programu, zadeklaruj dodatkowe zmienne Członkowskie w klasie okna dialogowego, aby obsłużyć te wartości wejściowe.

    > [!NOTE]
    >  Możesz dodać te zmienne Członkowskie przy użyciu menu kontekstowego w Widok klasy (zobacz [Dodawanie zmiennej składowej](../ide/adding-a-member-variable-visual-cpp.md)).

1. W [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) dla klasy okna dialogowego Ustaw początkowe warunki dla formantu wspólnego. Używając zmiennej składowej utworzonej w poprzednim kroku, użyj funkcji Członkowskich, aby ustawić wartość początkową i inne ustawienia. Aby uzyskać szczegółowe informacje na temat ustawień, zobacz następujące opisy kontrolek.

   Możesz również użyć [wymiany danych okna dialogowego](../mfc/dialog-data-exchange-and-validation.md) (DDX), aby zainicjować kontrolki w oknie dialogowym.

1. W przypadku kontrolek w oknie dialogowym, użyj zmiennej elementu członkowskiego, aby manipulować formantem. Aby uzyskać szczegółowe informacje na temat metod, zobacz następujące opisy kontrolek.

    > [!NOTE]
    >  Zmienna członkowska będzie istnieć tylko tak długo, jak samo okno dialogowe istnieje. Po zamknięciu okna dialogowego nie będzie można wykonać zapytania dotyczącego kontroli nad wartościami wejściowymi. Aby można było korzystać z wartości wejściowych ze wspólnej kontrolki, przesłonić `OnOK` w klasie okna dialogowego. W przesłonięciu wykonaj zapytanie dotyczące kontroli wartości wejściowych i Zapisz te wartości w zmiennych składowych klasy okna dialogowego.

    > [!NOTE]
    >  Możesz również użyć wymiany danych okna dialogowego, aby ustawić lub pobrać wartości z kontrolek w oknie dialogowym.

## <a name="remarks"></a>Uwagi

Dodanie niektórych typowych kontrolek do okna dialogowego spowoduje, że okno dialogowe przestanie działać. Zapoznaj się z [dodawaniem formantów do okna dialogowego powoduje, że okno dialogowe nie działa dłużej,](../windows/adding-editing-or-deleting-controls.md) Aby uzyskać więcej informacji na temat obsługi takiej sytuacji.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić

- [Dodaj kontrolki do okna dialogowego ręcznie zamiast z edytorem okien dialogowych](../mfc/adding-controls-by-hand.md)

- [Utwórz mój formant z jednej ze standardowych formantów wspólnych systemu Windows](../mfc/deriving-controls-from-a-standard-control.md)

- [Użyj formantu wspólnego jako okna podrzędnego](../mfc/using-a-common-control-as-a-child-window.md)

- [Otrzymywanie komunikatów powiadomień z kontrolki](../mfc/receiving-notification-from-common-controls.md)

- [Użyj wymiany danych okna dialogowego (DDX)](../mfc/dialog-data-exchange-and-validation.md)

## <a name="see-also"></a>Zobacz też

[Tworzenie i używanie kontrolek](../mfc/making-and-using-controls.md)<br/>
[Formanty](../mfc/controls-mfc.md)
