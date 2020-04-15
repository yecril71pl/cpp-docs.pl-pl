---
title: Implementowanie obszarów roboczych w formantach listy
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
ms.openlocfilehash: 91577203163247bd230fecb083cf1c50e2875b98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377224"
---
# <a name="implementing-working-areas-in-list-controls"></a>Implementowanie obszarów roboczych w formantach listy

Domyślnie formant listy rozmieszcza wszystkie elementy w standardowy sposób siatki. Jednak inna metoda jest obsługiwana, obszary robocze, który rozmieszcza elementy listy w grupach prostokątnych. Aby uzyskać obraz formantu listy implementujące obszary robocze, zobacz Używanie kontrolek widoku listy w zestawie Windows SDK.

> [!NOTE]
> Obszary robocze są widoczne tylko wtedy, gdy kontrolka listy jest w trybie ikony lub małej ikony. Jednak wszystkie bieżące obszary robocze są zachowywane, jeśli widok jest przełączony do trybu raportu lub listy.

Obszary robocze mogą być używane do wyświetlania pustej obramowania (po lewej, górnej i/lub prawej stronie elementów) lub powodować wyświetlanie poziomego paska przewijania, gdy zwykle nie ma go. Innym typowym zastosowaniem jest utworzenie wielu obszarów roboczych, do których elementy mogą być przenoszone lub upuszczane. Za pomocą tej metody można utworzyć obszary w jednym widoku, które mają różne znaczenia. Użytkownik może następnie kategoryzować elementy, umieszczając je w innym obszarze. Przykładem tego może być widok systemu plików, który ma obszar do odczytu/zapisu plików i inny obszar dla plików tylko do odczytu. Jeśli element pliku został przeniesiony do obszaru tylko do odczytu, automatycznie stanie się tylko do odczytu. Przeniesienie pliku z obszaru tylko do odczytu do obszaru odczytu/zapisu spowoduje, że plik odczytuje/zapis.

`CListCtrl`udostępnia kilka funkcji członkowskich do tworzenia i zarządzania obszarami roboczymi w formancie listy. [GetWorkAreas](../mfc/reference/clistctrl-class.md#getworkareas) i [SetWorkAreas](../mfc/reference/clistctrl-class.md#setworkareas) pobierają i `CRect` ustawiają `RECT` tablicę obiektów (lub struktur), które przechowują aktualnie zaimplementowane obszary robocze dla formantu listy. Ponadto [GetNumberOfWorkAreas](../mfc/reference/clistctrl-class.md#getnumberofworkareas) pobiera bieżącą liczbę obszarów roboczych dla formantu listy (domyślnie zero).

## <a name="items-and-working-areas"></a>Przedmioty i obszary robocze

Po utworzeniu obszaru roboczego elementy, które znajdują się w obszarze roboczym, stają się jego członkami. Podobnie, jeśli element zostanie przeniesiony do obszaru roboczego, staje się członkiem obszaru roboczego, do którego został przeniesiony. Jeśli element nie znajduje się w żadnym obszarze roboczym, automatycznie staje się członkiem pierwszego obszaru roboczego (indeks 0). Jeśli chcesz utworzyć element i umieścić go w określonym obszarze roboczym, musisz utworzyć element, a następnie przenieść go do żądanego obszaru roboczego za pomocą wywołania [SetItemPosition](../mfc/reference/clistctrl-class.md#setitemposition). Drugi przykład poniżej pokazuje tę technikę.

Poniższy przykład implementuje cztery`rcWorkAreas`obszary robocze ( ), o równej wielkości z obramowaniem o`m_WorkAreaListCtrl`szerokości 10 pikseli wokół każdego obszaru roboczego, w formancie listy ( ).

[!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

Wywołanie [ApproximateViewRect](../mfc/reference/clistctrl-class.md#approximateviewrect) zostało wykonane, aby uzyskać oszacowanie całkowitego obszaru wymaganego do wyświetlenia wszystkich elementów w jednym regionie. Oszacowanie to jest następnie podzielone na cztery regiony i wyściełane obramowaniem o szerokości 5 pikseli.

W następnym przykładzie przypisuje istniejące elementy`rcWorkAreas`listy do każdej grupy`m_WorkAreaListCtrl`( ) i odświeża widok sterowania ( ), aby zakończyć efekt.

[!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Formanty](../mfc/controls-mfc.md)
