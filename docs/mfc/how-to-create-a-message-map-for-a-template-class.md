---
title: 'Porady: tworzenie mapy komunikatów dla klasy szablonów'
ms.date: 11/04/2016
helpviewer_keywords:
- template classes [MFC], creating message maps
- message maps [MFC], template classes
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
ms.openlocfilehash: 65ddc77b4e8fd466c7d651e54e93a504b4858da1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620067"
---
# <a name="how-to-create-a-message-map-for-a-template-class"></a>Porady: tworzenie mapy komunikatów dla klasy szablonów

Mapowanie komunikatów w MFC zapewnia wydajny sposób kierowania komunikatów systemu Windows do odpowiedniego wystąpienia obiektu C++. Przykłady obiektów docelowych mapy komunikatów MFC obejmują klasy aplikacji, dokumenty i widoki, klasy formantów itd.

Tradycyjne mapy komunikatów MFC są deklarowane przy użyciu makra [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) , aby zadeklarować początek mapy komunikatów, wpis makra dla każdej metody klasy obsługi komunikatów, a wreszcie makro [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map) , aby zadeklarować koniec mapy komunikatów.

Jedno ograniczenie z makrem [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) występuje, gdy jest używane w połączeniu z klasą zawierającą argumenty szablonu. W przypadku użycia z klasą szablonu to makro spowoduje błąd czasu kompilacji z powodu braku parametrów szablonu podczas rozwinięcia makra. Makro [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map) zostało zaprojektowane w taki sposób, aby umożliwić klasom zawierającym jeden argument szablonu zadeklarować własne mapy komunikatów.

## <a name="example"></a>Przykład

Rozważmy przykład, w którym Klasa MFC [CListBox](reference/clistbox-class.md) jest rozszerzona, aby zapewnić synchronizację z zewnętrznym źródłem danych. Fikcyjna `CSyncListBox` Klasa jest zadeklarowana w następujący sposób:

[!code-cpp[NVC_MFC_CListBox#42](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_1.h)]

`CSyncListBox`Klasa jest szablonem na pojedynczym typie, który opisuje źródło danych, z którym zostanie ono zsynchronizowane. Deklaruje również trzy metody, które będą uczestniczyć w mapie wiadomości klasy: `OnPaint` , `OnDestroy` , i `OnSynchronize` . `OnSynchronize`Metoda jest implementowana w następujący sposób:

[!code-cpp[NVC_MFC_CListBox#43](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_2.cpp)]

Powyższa implementacja umożliwia `CSyncListBox` wyspecjalizowanie klasy dla dowolnego typu klasy, który implementuje `GetCount` metodę, taką jak `CArray` , `CList` , i `CMap` . `StringizeElement`Funkcja jest funkcją szablonu prototypową:

[!code-cpp[NVC_MFC_CListBox#44](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_3.cpp)]

Zwykle Mapa komunikatów dla tej klasy zostałaby zdefiniowana jako:

```cpp
BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)
  ON_WM_PAINT()
  ON_WM_DESTROY()
  ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)
END_MESSAGE_MAP()
```

gdzie **LBN_SYNCHRONIZE** to niestandardowa wiadomość użytkownika zdefiniowana przez aplikację, na przykład:

[!code-cpp[NVC_MFC_CListBox#45](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_4.cpp)]

Powyższe mapowanie makr nie zostanie skompilowane ze względu na fakt, że w trakcie rozwinięcia makra nie zostanie wykorzystana Specyfikacja szablonu dla `CSyncListBox` klasy. Makro **BEGIN_TEMPLATE_MESSAGE_MAP** rozwiązuje ten problem, dołączając określony parametr szablonu do rozwiniętej mapy makra. Mapa komunikatów dla tej klasy:

[!code-cpp[NVC_MFC_CListBox#46](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_5.cpp)]

Poniżej przedstawiono przykładowe użycie `CSyncListBox` klasy przy użyciu `CStringList` obiektu:

[!code-cpp[NVC_MFC_CListBox#47](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_6.cpp)]

Aby ukończyć test, `StringizeElement` Funkcja musi być wyspecjalizowana do pracy z `CStringList` klasą:

[!code-cpp[NVC_MFC_CListBox#48](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_7.cpp)]

## <a name="see-also"></a>Zobacz też

[BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)<br/>
[Obsługa i mapowanie komunikatów](message-handling-and-mapping.md)
