---
title: Arkusze właściwości jako kreatorzy
ms.date: 11/04/2016
helpviewer_keywords:
- property sheets, as wizards
ms.assetid: 1ea66ecb-23b0-484a-838d-58671a2999b5
ms.openlocfilehash: e8ba740d31681de214d2a497bc2694a94d09d84d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542626"
---
# <a name="property-sheets-as-wizards"></a>Arkusze właściwości jako kreatorzy

Jedną z najważniejszych cech arkusz właściwości Kreator jest nawigacji jest udostępniany przycisków Dalej lub Zakończ Wstecz i Anuluj zamiast tabulatorów. Należy wywołać [CPropertySheet::SetWizardMode](../mfc/reference/cpropertysheet-class.md#setwizardmode) przed wywołaniem [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal) na obiekt arkusza właściwości, aby móc korzystać z tej funkcji.

Użytkownik otrzymuje taki sam [CPropertyPage::OnSetActive](../mfc/reference/cpropertypage-class.md#onsetactive) i [CPropertyPage::OnKillActive](../mfc/reference/cpropertypage-class.md#onkillactive) powiadomienia podczas przenoszenia z jednej strony do innej strony. Dalej i Zakończ przyciski są formanty wzajemnie się wykluczają; oznacza to, że tylko jeden z nich pojawią się w danym momencie. Na pierwszej stronie można włączyć przycisk Dalej. Jeśli użytkownik znajduje się na ostatniej stronie, powinno być włączone przycisk Zakończ. Nie jest to wykonywane automatycznie przez platformę. Trzeba wywoływać [CPropertySheet::SetWizardButton](../mfc/reference/cpropertysheet-class.md#setwizardbuttons) na ostatniej stronie, aby to osiągnąć.

Aby wyświetlić wszystkie przyciski domyślne, możesz mush Pokaż przycisk Zakończ i Przenieś przycisk Dalej. Następnie przenieś przycisk Wstecz, utrzymywanie jej położenie względne, do przycisk Dalej.

## <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#5](../mfc/codesnippet/cpp/property-sheets-as-wizards_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Arkusze właściwości](../mfc/property-sheets-mfc.md)

