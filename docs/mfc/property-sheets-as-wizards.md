---
title: Arkusze właściwości jako kreatorzy
ms.date: 11/04/2016
helpviewer_keywords:
- property sheets, as wizards
ms.assetid: 1ea66ecb-23b0-484a-838d-58671a2999b5
ms.openlocfilehash: c60148c099b34993bef0c9808e6561e37c26cc7f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301678"
---
# <a name="property-sheets-as-wizards"></a>Arkusze właściwości jako kreatorzy

Jedną z najważniejszych cech arkusz właściwości Kreator jest nawigacji jest udostępniany przycisków Dalej lub Zakończ Wstecz i Anuluj zamiast tabulatorów. Należy wywołać [CPropertySheet::SetWizardMode](../mfc/reference/cpropertysheet-class.md#setwizardmode) przed wywołaniem [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal) na obiekt arkusza właściwości, aby móc korzystać z tej funkcji.

Użytkownik otrzymuje taki sam [CPropertyPage::OnSetActive](../mfc/reference/cpropertypage-class.md#onsetactive) i [CPropertyPage::OnKillActive](../mfc/reference/cpropertypage-class.md#onkillactive) powiadomienia podczas przenoszenia z jednej strony do innej strony. Dalej i Zakończ przyciski są formanty wzajemnie się wykluczają; oznacza to, że tylko jeden z nich pojawią się w danym momencie. Na pierwszej stronie można włączyć przycisk Dalej. Jeśli użytkownik znajduje się na ostatniej stronie, powinno być włączone przycisk Zakończ. Nie jest to wykonywane automatycznie przez platformę. Trzeba wywoływać [CPropertySheet::SetWizardButton](../mfc/reference/cpropertysheet-class.md#setwizardbuttons) na ostatniej stronie, aby to osiągnąć.

Aby wyświetlić wszystkie przyciski domyślne, możesz mush Pokaż przycisk Zakończ i Przenieś przycisk Dalej. Następnie przenieś przycisk Wstecz, utrzymywanie jej położenie względne, do przycisk Dalej.

## <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#5](../mfc/codesnippet/cpp/property-sheets-as-wizards_1.cpp)]

## <a name="see-also"></a>Zobacz także

[Arkusze właściwości](../mfc/property-sheets-mfc.md)
