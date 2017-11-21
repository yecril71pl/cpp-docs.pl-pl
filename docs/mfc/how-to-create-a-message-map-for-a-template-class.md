---
title: "Porady: Tworzenie mapy komunikatów dla klasy szablonów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- template classes [MFC], creating message maps
- message maps [MFC], template classes
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 73f6812b1dcc4652c1cb984ddb0ca67f3e72f631
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-create-a-message-map-for-a-template-class"></a>Porady: tworzenie mapy komunikatów dla klasy szablonów
Mapowanie komunikatów w MFC zapewnia efektywną bezpośrednie komunikaty systemu Windows do odpowiedniego wystąpienia obiektu języka C++. Przykładami cele mapy komunikatów MFC klasy aplikacji, dokumentów i widoku klasy, klasy formantów i tak dalej.  
  
 Mapy komunikatów MFC tradycyjnych zadeklarowane za pomocą [begin_message_map —](reference/message-map-macros-mfc.md#begin_message_map) makra, aby zadeklarować początku mapę komunikatów wpisem makro dla każdej metody klasy obsługi wiadomości i w końcu [end_message_map —](reference/message-map-macros-mfc.md#end_message_map)makra, aby zadeklarować koniec mapy komunikatów.  
  
 Jednym z ograniczeń z [begin_message_map —](reference/message-map-macros-mfc.md#begin_message_map) makro występuje, gdy jest używany w połączeniu z klasa zawierająca argumentów szablonu. W przypadku użycia z klasy szablonu, to makro spowoduje błąd kompilacji ze względu na Brak parametrów szablonu w rozwinięciu makra. [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map) — makro zaprojektowano tak, aby umożliwić mapuje klasy zawierające argument jednego szablonu, aby zadeklarować własnych wiadomości.  
  
## <a name="example"></a>Przykład  
 Rozważ przykład gdzie MFC [clistbox —](../mfc/reference/clistbox-class.md) klasa jest rozszerzona, aby zapewnić synchronizację z zewnętrznego źródła danych. Fikcyjne **CSyncListBox** klasy jest zadeklarowany w następujący sposób:  
  
 [!code-cpp[NVC_MFC_CListBox#42](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_1.h)]  
  
 **CSyncListBox** klasa znajduje się na jednym typie, który opisuje źródła danych zostaną zsynchronizowane z szablonem. Również deklaruje trzy metody, które będą uczestniczyć w mapie komunikatów klasy: **OnPaint**, **OnDestroy**, i **OnSynchronize**. **OnSynchronize** metoda jest zaimplementowana w następujący sposób:  
  
 [!code-cpp[NVC_MFC_CListBox#43](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_2.cpp)]  
  
 Umożliwia wykonania powyższych **CSyncListBox** klasy być specjalizowany w dowolnego typu klasy, który implementuje **GetCount** metody, takie jak **carray —**, **Clist —**, i **CMap**. **StringizeElement** funkcja jest funkcją szablonu prototypowana co następuje:  
  
 [!code-cpp[NVC_MFC_CListBox#44](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_3.cpp)]  
  
 Zazwyczaj mapy komunikatów dla tej klasy może być zdefiniowana jako:  
  
 `BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)`  
  
 `ON_WM_PAINT()`  
  
 `ON_WM_DESTROY()`  
  
 `ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)`  
  
 `END_MESSAGE_MAP()`  
  
 gdzie **LBN_SYNCHRONIZE** komunikat użytkownika niestandardowego zdefiniowane przez aplikację, takich jak:  
  
 [!code-cpp[NVC_MFC_CListBox#45](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_4.cpp)]  
  
 Powyżej mapy makro nie zostanie skompilowany, wynika z faktu, że w specyfikacji szablonu **CSyncListBox** klasy będą niedostępne w rozwinięciu makra. **BEGIN_TEMPLATE_MESSAGE_MAP** makro rozwiązuje ten problem, dołączając parametr określonego szablonu do mapy makro rozwinięte. Staje się mapy komunikatów dla tej klasy:  
  
 [!code-cpp[NVC_MFC_CListBox#46](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_5.cpp)]  
  
 Następujące przedstawiono przykładowe użycie **CSyncListBox** przy użyciu **CStringList** obiektu:  
  
 [!code-cpp[NVC_MFC_CListBox#47](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_6.cpp)]  
  
 Aby ukończyć test, **StringizeElement** funkcja musi być specjalizowany do pracy z **CStringList** klasy:  
  
 [!code-cpp[NVC_MFC_CListBox#48](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_7.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)   
 [Obsługa i mapowanie komunikatów](../mfc/message-handling-and-mapping.md)

