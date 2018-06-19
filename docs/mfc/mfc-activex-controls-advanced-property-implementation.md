---
title: 'Kontrolki ActiveX MFC: Implementacja właściwości zaawansowanych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97b6bbcbcf226d343d8b3cb51f110442e133a379
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351842"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>Kontrolki ActiveX MFC: implementacja właściwości zaawansowanych
W tym artykule opisano tematy związane z implementacją zaawansowane właściwości formantu ActiveX:  
  
-   [Właściwości tylko do odczytu i tylko do zapisu](#_core_read2donly_and_write2donly_properties)  
  
-   [Zwracanie kodów błędów z właściwością](#_core_returning_error_codes_from_a_property)  
  
##  <a name="_core_read2donly_and_write2donly_properties"></a> Właściwości tylko do odczytu i tylko do zapisu  
 Kreator dodawania właściwości zapewnia szybki i łatwy sposób zaimplementowane właściwości tylko do odczytu lub w trybie tylko do zapisu dla formantu.  
  
#### <a name="to-implement-a-read-only-or-write-only-property"></a>Aby zaimplementować właściwości tylko do odczytu lub w trybie tylko do zapisu  
  
1.  Załaduj projekt z kontroli.  
  
2.  W widoku klas rozwiń węzeł Biblioteka formantu.  
  
3.  Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugiego węzła węzeł biblioteki), aby otworzyć menu skrótów.  
  
4.  W menu skrótów kliknij **Dodaj** , a następnie kliknij przycisk **Dodaj właściwość**.  
  
     Spowoduje to otwarcie [Dodaj Kreatora właściwości](../ide/names-add-property-wizard.md).  
  
5.  W **nazwa właściwości** wpisz nazwę programu właściwości.  
  
6.  Aby uzyskać **typ implementacji**, kliknij przycisk **metod Get/Set**.  
  
7.  W **typ właściwości** wybierz odpowiedniego typu właściwości.  
  
8.  Jeśli chcesz, aby właściwość tylko do odczytu, wyczyść nazwą zestawu funkcji. Jeśli chcesz, aby właściwość tylko do zapisu, wyczyść Get nazwy funkcji.  
  
9. Kliknij przycisk **Zakończ**.  
  
 Po wykonaniu tej czynności w Kreatorze dodawania właściwości Wstawia funkcję `SetNotSupported` lub `GetNotSupported` we wpisie mapy wysyłania zamiast zwykłym ustawiać ani pobierać funkcji.  
  
 Jeśli chcesz zmienić istniejącej właściwości tylko do odczytu lub tylko do zapisu, można ręcznie edytować mapy wysyłania i usunąć niepotrzebne funkcja Set lub Get z klasy formantu.  
  
 Jeśli chcesz, aby właściwość, która ma być warunkowo tylko do odczytu lub tylko do zapisu (na przykład tylko wtedy, gdy formant działa w określonym trybie), można podać funkcję Set lub Get, jak zwykle i Wywołaj `SetNotSupported` lub `GetNotSupported` funkcji w miarę potrzeb. Na przykład:  
  
 [!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]  
  
 Ten przykładowy kod wywołuje `SetNotSupported` Jeśli `m_bReadOnlyMode` elementu członkowskiego danych jest **TRUE**. Jeśli **FALSE**, a następnie właściwość jest ustawiona na nową wartość.  
  
##  <a name="_core_returning_error_codes_from_a_property"></a> Zwracanie kodów błędów z właściwością  
 Aby wskazać, że wystąpił błąd podczas próby pobrania lub ustaw właściwość, użyj `COleControl::ThrowError` funkcja, która przyjmuje `SCODE` (kod stanu) jako parametr. Można użyć wstępnie zdefiniowanej `SCODE` lub zdefiniuj własny. Lista wstępnie zdefiniowanych `SCODE`s i instrukcje dotyczące definiowania niestandardowych `SCODE`s, zobacz [obsługi błędów w tym formancie ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) w artykule formantów ActiveX: Tematy zaawansowane.  
  
 Funkcje pomocy istnieje dla najbardziej typowe wstępnie zdefiniowane `SCODE`s, takich jak [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), i [colecontrol —:: SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).  
  
> [!NOTE]
>  `ThrowError` ma być używane tylko jako środek zwróci błąd w wartości właściwości Get lub Set z metody automatyzacji lub funkcji. Są to jedyna razy, które będą program obsługi wyjątku odpowiednie znajduje się on na stosie.  
  
 Aby uzyskać więcej informacji na wyjątki w innych obszarach kodu raportowania, zobacz [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) i sekcji [obsługi błędów w tym formancie ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) w artykule formantów ActiveX: Zaawansowane Tematy.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Formanty MFC ActiveX: właściwości](../mfc/mfc-activex-controls-properties.md)   
 [Formanty MFC ActiveX: metody](../mfc/mfc-activex-controls-methods.md)   
 [Klasa COleControl](../mfc/reference/colecontrol-class.md)
