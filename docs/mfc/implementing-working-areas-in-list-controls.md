---
title: Implementowanie obszarów roboczych w kontrolkach listy
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
ms.openlocfilehash: eac4c28497f4a00a333f5396fa71cdb2176106c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525200"
---
# <a name="implementing-working-areas-in-list-controls"></a>Implementowanie obszarów roboczych w kontrolkach listy

Domyślnie formant listy Rozmieszcza elementy w sposób standardowy siatki. Inną metodą jest jednak obsługiwane, praca obszary Rozmieszcza elementy listy na grupy prostokątny. W przypadku obrazu kontrolkę listy, która implementuje obszary robocze, zobacz za pomocą kontrolki widok listy w zestawie Windows SDK.

> [!NOTE]
>  Obszary robocze są widoczne tylko wtedy, gdy kontrolka listy w trybie mała ikona lub ikonę. Jednak wszelkie bieżące obszary robocze są obsługiwane, jeśli widok jest przełączony do trybu raportu lub listy.

Obszary robocze może służyć do zobrazit pusty obramowania (po lewej stronie, top lub po prawej stronie elementy) lub spowodować, że poziomy pasek przewijania będzie wyświetlana po zwykle nie istnieć tylko jeden. Inny wspólne użycie polega na utworzeniu wielu obszary robocze, do których elementów można przeniesiony lub usunięty. Przy użyciu tej metody można tworzyć obszary, w ramach jednego widoku, które mają różne znaczenie. Użytkownik może następnie skategoryzować elementy, umieszczając je w innej strefie. Na przykład będzie widok systemu plików, które ma odczytu/zapisu plików i innego obszaru dla plików tylko do odczytu. Jeśli element pliku zostały przeniesione do obszaru tylko do odczytu, go czy automatycznie stają się one tylko do odczytu. Przenoszenie plików z obszaru tylko do odczytu do obszaru odczytu/zapisu czy upewnij, że plik odczytu/zapisu.

`CListCtrl` udostępnia kilka funkcji elementów członkowskich do tworzenia i zarządzania obszary robocze w kontrolce listy. [GetWorkAreas](../mfc/reference/clistctrl-class.md#getworkareas) i [SetWorkAreas](../mfc/reference/clistctrl-class.md#setworkareas) pobierać i ustawiać tablicę `CRect` obiektów (lub `RECT` struktury), który przechowywania aktualnie wdrożonych obszary robocze dla kontrolki listy. Ponadto [GetNumberOfWorkAreas](../mfc/reference/clistctrl-class.md#getnumberofworkareas) pobiera bieżącą liczbę obszary robocze dla kontrolki listy (domyślnie przez zero).

## <a name="items-and-working-areas"></a>Elementy i obszarów roboczych

Po utworzeniu obszaru roboczego elementy, które znajdują się w obszarze roboczym stają się jej członkowie. Podobnie jeśli element zostanie przeniesiony do obszaru roboczego, staje się członkiem obszaru roboczego, do którego został przeniesiony. Jeśli element nie leży w dowolnym obszarze roboczym, staje się automatycznie członkiem pierwszy obszar roboczy (indeks 0). Jeśli chcesz utworzyć element i jest umieszczany w ramach określonego obszaru roboczego, konieczne będzie utwórz go, a następnie przenieś go do żądanego obszaru roboczego z wywołaniem [SetItemPosition](../mfc/reference/clistctrl-class.md#setitemposition). Drugi przykład poniżej pokazano tej techniki.

Poniższy przykład implementuje czterech obszarów roboczych (`rcWorkAreas`), taki sam rozmiar z 10 pikseli całego obramowania wokół każdego obszaru roboczego w kontrolce listy (`m_WorkAreaListCtrl`).

[!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

Wywołanie [ApproximateViewRect](../mfc/reference/clistctrl-class.md#approximateviewrect) została wprowadzona, aby poznać szacunkową całkowitego obszaru, które są wymagane, aby wyświetlić wszystkie elementy w jednym regionie. Te dane szacunkowe następnie jest podzielony na cztery obszary i dopełniane przy użyciu obramowania 5 pikseli na poziomie.

Następny przykład przypisuje istniejących elementów listy do każdej grupy (`rcWorkAreas`) oraz odświeżenie widoku formantu (`m_WorkAreaListCtrl`) do ukończenia efekt.

[!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

