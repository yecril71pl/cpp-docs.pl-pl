---
title: Używanie formantów wspólnych w oknie dialogowym
ms.date: 11/04/2016
helpviewer_keywords:
- common controls [MFC], in dialog boxes
- dialog box controls [MFC], common controls
- Windows common controls [MFC], in dialog boxes
ms.assetid: 17713caf-09f8-484a-bf54-5f48bf09cce9
ms.openlocfilehash: ade1b464d3851fb9294a1ba7180b48771f0468cc
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259194"
---
# <a name="using-common-controls-in-a-dialog-box"></a>Używanie formantów wspólnych w oknie dialogowym

Formanty standardowe Windows mogą być używane w [okna dialogowe](../mfc/dialog-boxes.md), tworzą, widoki, widoki rekordów i inne okno na podstawie szablonu okna dialogowego. Wykonanie poniższej procedury z drobnymi zmianami będzie działać w przypadku form, jak również.

## <a name="procedures"></a>Procedury

#### <a name="to-use-a-common-control-in-a-dialog-box"></a>Aby użyć wspólne kontrolki w oknie dialogowym

1. Umieść formant na szablonu okna dialogowego [przy użyciu edytora okien dialogowych](../mfc/using-the-dialog-editor-to-add-controls.md).

1. Dodaj do klasy okien dialogowych zmiennej członkowskiej, która reprezentuje kontrolkę. W **Dodawanie zmiennej członkowskiej** okno dialogowe wyboru **zmienna sterująca** i upewnij się, że **kontroli** wybrano **kategorii**.

1. Jeśli tego formantu typowego jest podanie danych wejściowych do programu, należy zadeklarować członka dodatkowe variable(s) w klasy okien dialogowych, aby obsłużyć te wartości wejściowe.

    > [!NOTE]
    >  Możesz dodać te zmienne Członkowskie przy użyciu menu kontekstowego w widoku klas (zobacz [dodawania zmiennej składowej](../ide/adding-a-member-variable-visual-cpp.md)).

1. W [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) dla klasy okien dialogowych, ustawić warunków początkowych wspólnej kontroli. Używanie zmiennej składowej, utworzony w poprzednim kroku, należy użyć funkcji elementów członkowskich można ustawić wartość początkową i inne ustawienia. Zobacz poniższe opisy kontrolek, aby uzyskać szczegółowe informacje na temat ustawień.

   Można również użyć [wymiana danych okna dialogowego](../mfc/dialog-data-exchange-and-validation.md) (DDX), aby zainicjować kontrolki w oknie dialogowym.

1. W procedurach obsługi dla formantów w oknie dialogowym należy użyć zmiennej składowej do manipulowania formantu. Zobacz poniższe opisy kontrolek, aby uzyskać szczegółowe informacje na temat metod.

    > [!NOTE]
    >  Zmiennej składowej będzie istnieć tylko tak długo, jak okno dialogowe, sam istnieje. Nie można zbadać formantu dla wartości wejściowych, po zamknięciu okna dialogowego. Aby pracować z wartości wejściowe z formantu wspólnego, należy zastąpić `OnOK` w klasy okien dialogowych. W przesłonięcia zapytanie formantu dla wartości wejściowych i przechowywania tych wartości w zmiennych elementu członkowskiego klasy okna dialogowego.

    > [!NOTE]
    >  Wymiana danych okna dialogowego umożliwia również ustawić lub pobrać wartości z kontrolek w oknie dialogowym.

## <a name="remarks"></a>Uwagi

Dodanie niektórych wspólnych formantów do okna dialogowego spowoduje, że okno dialogowe przestanie działać. Zapoznaj się [dodawanie formantów do okna dialogowego powoduje, że okno dialogowe funkcji niebędących](../windows/adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function.md) więcej informacji na temat obsługi tej sytuacji.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić

- [Dodawanie formantów do okna dialogowego ręcznie zamiast przy użyciu edytora okien dialogowych](../mfc/adding-controls-by-hand.md)

- [Klasy pochodnej mój formant z jednego standardowego wspólnych formantów Windows](../mfc/deriving-controls-from-a-standard-control.md)

- [Używanie formantu wspólnego jako okna podrzędnego](../mfc/using-a-common-control-as-a-child-window.md)

- [Odbieranie komunikatów powiadomień w kontrolce](../mfc/receiving-notification-from-common-controls.md)

- [Użyj wymiana danych okna dialogowego (DDX)](../mfc/dialog-data-exchange-and-validation.md)

## <a name="see-also"></a>Zobacz także

[Tworzenie i używanie kontrolek](../mfc/making-and-using-controls.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
