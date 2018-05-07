---
title: Arkusze właściwości jako kreatorzy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property sheets, as wizards
ms.assetid: 1ea66ecb-23b0-484a-838d-58671a2999b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 634359763f24e02987664fe3de1094e3e7fec64c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="property-sheets-as-wizards"></a>Arkusze właściwości jako kreatorzy
Klucza cech arkusz właściwości Kreatora to, czy nawigacji podano za pomocą przycisków Dalej lub Zakończ Wstecz i Anuluj zamiast tabulatorów. Należy wywołać [CPropertySheet::SetWizardMode](../mfc/reference/cpropertysheet-class.md#setwizardmode) przed wywołaniem [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal) na obiekt arkusza właściwości, aby móc korzystać z tej funkcji.  
  
 Użytkownik otrzymuje takie same [CPropertyPage::OnSetActive](../mfc/reference/cpropertypage-class.md#onsetactive) i [CPropertyPage::OnKillActive](../mfc/reference/cpropertypage-class.md#onkillactive) powiadomienia podczas przenoszenia z jednej strony do innej strony. Przyciski Zakończ i dalej są wzajemnie kontroli; oznacza to tylko jeden z nich ma być wyświetlany w danym momencie. Na pierwszej stronie powinien być włączony przycisk Dalej. Jeśli użytkownik znajduje się na ostatniej stronie, powinien być włączony przycisk Zakończ. Nie odbywa się automatycznie przez platformę. Należy wywołać [CPropertySheet::SetWizardButton](../mfc/reference/cpropertysheet-class.md#setwizardbuttons) na ostatniej stronie, aby to osiągnąć.  
  
 Aby wyświetlić wszystkie domyślnych przycisków, mush możesz wyświetlać przycisk Zakończ i Przenieś przycisk Dalej. Następnie przenieś przycisk Wstecz, utrzymywanie jej względne położenie przycisku Dalej.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#5](../mfc/codesnippet/cpp/property-sheets-as-wizards_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Arkusze właściwości](../mfc/property-sheets-mfc.md)

