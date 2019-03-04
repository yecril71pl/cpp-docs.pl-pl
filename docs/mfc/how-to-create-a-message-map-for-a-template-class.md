---
title: 'Instrukcje: Tworzenie mapy komunikatów dla klasy szablonów'
ms.date: 11/04/2016
helpviewer_keywords:
- template classes [MFC], creating message maps
- message maps [MFC], template classes
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
ms.openlocfilehash: 676e698a899327eee8305731b5d609b5b95ece76
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296777"
---
# <a name="how-to-create-a-message-map-for-a-template-class"></a>Instrukcje: Tworzenie mapy komunikatów dla klasy szablonów

Mapowanie komunikatów w MFC zapewnia skuteczny sposób przekierowywania komunikatów Windows odpowiednie wystąpienia obiektu języka C++. Przykłady celów mapy komunikatów MFC klasy aplikacji, dokument i widok klasy, klasy kontrolek i tak dalej.

Tradycyjne mapy komunikatów MFC są deklarowane przy użyciu [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) makra, aby zadeklarować początek mapie komunikatów wpis — makro dla poszczególnych metod klasy programu obsługi komunikatów, a na koniec [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)makra, aby zadeklarować koniec mapie komunikatów.

Jednym z ograniczeń za pomocą [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) makra występuje, gdy jest używany w połączeniu z klasą zawierającą argumenty szablonu. Używane z klasą szablonu, to makro spowoduje błąd kompilacji, ze względu na brakujące parametry szablonu w rozwinięciu makra. [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map) — makro zaprojektowano tak, aby umożliwić mapuje klasy zawierające argument jednego szablonu do deklarowania własne wiadomości.

## <a name="example"></a>Przykład

Rozważmy przykład, gdzie MFC [CListBox](../mfc/reference/clistbox-class.md) klasa jest rozszerzona zapewnienie synchronizacji z zewnętrznego źródła danych. Fikcyjnej `CSyncListBox` klasy jest zadeklarowana w następujący sposób:

[!code-cpp[NVC_MFC_CListBox#42](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_1.h)]

`CSyncListBox` Klasa jest oparte na szablonach na jednym typie, który opisuje źródła danych zostaną zsynchronizowane z. Deklaruje również trzy metody, które będą uczestniczyć w mapie komunikatów klasy: `OnPaint`, `OnDestroy`, i `OnSynchronize`. `OnSynchronize` Metoda jest implementowana w następujący sposób:

[!code-cpp[NVC_MFC_CListBox#43](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_2.cpp)]

Zezwala na wykonanie powyższych `CSyncListBox` klasy można wyspecjalizować z każdym typem klasy, która implementuje `GetCount` metody, takie jak `CArray`, `CList`, i `CMap`. `StringizeElement` Funkcja jest funkcją szablonu prototypowane przez następujące:

[!code-cpp[NVC_MFC_CListBox#44](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_3.cpp)]

Mapy komunikatów dla tej klasy będzie zazwyczaj zdefiniowane jako:

```cpp
BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)
  ON_WM_PAINT()
  ON_WM_DESTROY()
  ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)
END_MESSAGE_MAP()
```

gdzie **LBN_SYNCHRONIZE** komunikat użytkownika niestandardowego zdefiniowany przez aplikację, takie jak:

[!code-cpp[NVC_MFC_CListBox#45](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_4.cpp)]

Powyżej mapy — makro nie zostanie skompilowany, wynika z faktu, że w specyfikacji szablonu `CSyncListBox` klasy będą niedostępne w rozwinięciu makra. **BEGIN_TEMPLATE_MESSAGE_MAP** — makro rozwiązuje ten problem, dołączając parametru określonego szablonu do mapy rozwiniętej — makro. Staje się mapy komunikatów dla tej klasy:

[!code-cpp[NVC_MFC_CListBox#46](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_5.cpp)]

Następujące przedstawiono przykładowe zastosowanie `CSyncListBox` przy użyciu `CStringList` obiektu:

[!code-cpp[NVC_MFC_CListBox#47](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_6.cpp)]

Aby ukończyć test, `StringizeElement` — funkcja musi być przeznaczone specjalnie do pracy z `CStringList` klasy:

[!code-cpp[NVC_MFC_CListBox#48](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_7.cpp)]

## <a name="see-also"></a>Zobacz także

[BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)<br/>
[Obsługa i mapowanie komunikatów](../mfc/message-handling-and-mapping.md)
