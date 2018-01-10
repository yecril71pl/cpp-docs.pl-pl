---
title: "Arkusze właściwości jako kreatorzy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: property sheets, as wizards
ms.assetid: 1ea66ecb-23b0-484a-838d-58671a2999b5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 65aedc5dbeb8a740d5713983f66eefe693864937
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="property-sheets-as-wizards"></a>Arkusze właściwości jako kreatorzy
Klucza cech arkusz właściwości Kreatora to, czy nawigacji podano za pomocą przycisków Dalej lub Zakończ Wstecz i Anuluj zamiast tabulatorów. Należy wywołać [CPropertySheet::SetWizardMode](../mfc/reference/cpropertysheet-class.md#setwizardmode) przed wywołaniem [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal) na obiekt arkusza właściwości, aby móc korzystać z tej funkcji.  
  
 Użytkownik otrzymuje takie same [CPropertyPage::OnSetActive](../mfc/reference/cpropertypage-class.md#onsetactive) i [CPropertyPage::OnKillActive](../mfc/reference/cpropertypage-class.md#onkillactive) powiadomienia podczas przenoszenia z jednej strony do innej strony. Przyciski Zakończ i dalej są wzajemnie kontroli; oznacza to tylko jeden z nich ma być wyświetlany w danym momencie. Na pierwszej stronie powinien być włączony przycisk Dalej. Jeśli użytkownik znajduje się na ostatniej stronie, powinien być włączony przycisk Zakończ. Nie odbywa się automatycznie przez platformę. Należy wywołać [CPropertySheet::SetWizardButton](../mfc/reference/cpropertysheet-class.md#setwizardbuttons) na ostatniej stronie, aby to osiągnąć.  
  
 Aby wyświetlić wszystkie domyślnych przycisków, mush możesz wyświetlać przycisk Zakończ i Przenieś przycisk Dalej. Następnie przenieś przycisk Wstecz, utrzymywanie jej względne położenie przycisku Dalej.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#5](../mfc/codesnippet/cpp/property-sheets-as-wizards_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Arkusze właściwości](../mfc/property-sheets-mfc.md)

