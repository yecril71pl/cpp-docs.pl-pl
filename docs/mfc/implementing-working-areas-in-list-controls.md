---
title: Implementowanie obszarów roboczych w formantach listy
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], working areas
- working areas in list control [MFC]
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
ms.openlocfilehash: abbf9dd823e13fab252b7af8f32338b0d801079b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626376"
---
# <a name="implementing-working-areas-in-list-controls"></a>Implementowanie obszarów roboczych w formantach listy

Domyślnie kontrolka listy Rozmieszcza wszystkie elementy w standardowej siatce. Jednak inna metoda jest obsługiwana, obszary robocze, które układają elementy listy w prostokątne grupy. Aby uzyskać obraz formantu listy, który implementuje obszary robocze, zobacz Używanie kontrolek widok listy w Windows SDK.

> [!NOTE]
> Obszary robocze są widoczne tylko wtedy, gdy kontrolka listy jest w trybie ikon lub małych ikon. Jednak wszystkie bieżące obszary robocze są utrzymywane, gdy widok zostanie przełączony do trybu raportu lub listy.

Obszary robocze mogą być używane do wyświetlania pustego obramowania (po lewej, górnej i/lub prawej części elementów) lub spowodować, że poziomy pasek przewijania ma być wyświetlany, gdy zwykle nie będzie to możliwe. Innym typowym użyciem jest utworzenie wielu obszarów roboczych, do których można przenieść lub porzucić elementy. Za pomocą tej metody można tworzyć obszary w jednym widoku, które mają różne znaczenie. Użytkownik może następnie klasyfikować elementy, umieszczając je w innym obszarze. Przykładem może być widok systemu plików, który ma obszar dla plików odczytu/zapisu i inny obszar dla plików tylko do odczytu. Jeśli element pliku został przeniesiony do obszaru tylko do odczytu, będzie on automatycznie tylko do odczytu. Przeniesienie pliku z obszaru tylko do odczytu do obszaru odczytu/zapisu spowoduje, że plik zostanie odczytany/zapisany.

`CListCtrl`Program udostępnia kilka funkcji Członkowskich do tworzenia obszarów roboczych i zarządzania nimi w kontrolce listy. [GetWorkAreas](reference/clistctrl-class.md#getworkareas) i [SetWorkAreas](reference/clistctrl-class.md#setworkareas) pobierają i ustawiają tablicę `CRect` obiektów (lub `RECT` struktur), które przechowują aktualnie zaimplementowane obszary robocze dla formantu listy. Ponadto [GetNumberOfWorkAreas](reference/clistctrl-class.md#getnumberofworkareas) pobiera bieżącą liczbę obszarów roboczych dla kontrolki listy (domyślnie zero).

## <a name="items-and-working-areas"></a>Elementy i obszary robocze

Po utworzeniu obszaru roboczego elementy, które znajdują się w obszarze roboczym, stają się elementami członkowskimi. Podobnie, jeśli element zostanie przeniesiony do obszaru roboczego, zostaje on członkiem obszaru roboczego, do którego został przeniesiony. Jeśli element nie znajduje się w żadnym obszarze roboczym, automatycznie stał się członkiem pierwszego (indeks 0) obszaru roboczego. Jeśli chcesz utworzyć element i umieścić go w określonym obszarze roboczym, musisz utworzyć element, a następnie przenieść go do odpowiedniego obszaru roboczego z wywołaniem do [SetItemPosition](reference/clistctrl-class.md#setitemposition). W drugim przykładzie poniżej pokazano tę technikę.

Poniższy przykład implementuje cztery obszary robocze ( `rcWorkAreas` ) o równym rozmiarze z obramowaniem o szerokości 10 pikseli wokół każdego obszaru roboczego, w kontrolce listy ( `m_WorkAreaListCtrl` ).

[!code-cpp[NVC_MFCControlLadenDialog#20](codesnippet/cpp/implementing-working-areas-in-list-controls_1.cpp)]

Wywołanie [ApproximateViewRect](reference/clistctrl-class.md#approximateviewrect) zostało wykonane w celu uzyskania oszacowania łącznego obszaru wymaganego do wyświetlenia wszystkich elementów w jednym regionie. To oszacowanie jest następnie podzielone na cztery regiony i uzupełnione o 5 pikseli szerokości.

Następny przykład przypisuje istniejące elementy listy do każdej grupy ( `rcWorkAreas` ) i odświeża widok formantu ( `m_WorkAreaListCtrl` ) w celu ukończenia tego efektu.

[!code-cpp[NVC_MFCControlLadenDialog#21](codesnippet/cpp/implementing-working-areas-in-list-controls_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Korzystanie z CListCtrl](using-clistctrl.md)<br/>
[Formanty](controls-mfc.md)
