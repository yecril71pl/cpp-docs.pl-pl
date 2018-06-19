---
title: Zalecenia dotyczące wybierania klasy kolekcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- type safety of collection classes [MFC]
- collection classes [MFC], serialization
- collection classes [MFC], speed
- collection classes [MFC], type safety
- collection classes [MFC], choosing
- collection classes [MFC], functionality
- shapes, collection
- collection classes [MFC], template-based
- MFC collection classes [MFC], characteristics
- collection classes [MFC], about collection classes [MFC]
- serialization [MFC], collection classes
- collection classes [MFC], duplicates allowed
- collection classes [MFC], shapes
ms.assetid: a82188cd-443f-40d8-a244-edf292a53db4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 28527f9668b9ca6a9ef00cf399a04ce9bad65716
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353135"
---
# <a name="recommendations-for-choosing-a-collection-class"></a>Zalecenia dotyczące wybierania klasy kolekcji
Ten artykuł zawiera szczegółowe informacje ułatwiające wybieranie klasy kolekcji do potrzeb aplikacji.  
  
 Wybrana klasa kolekcji zależy od wielu czynników, takich jak:  
  
-   Funkcje klasy kształtu: kolejność, indeksowanie i wydajności, jak pokazano w [kolekcji elementów kształtu](#_core_collection_shape_features) tabeli w dalszej części tego tematu  
  
-   Określa, czy klasa korzysta z szablonów języka C++  
  
-   Określa, czy może być Zserializowany elementy przechowywane w kolekcji  
  
-   Określa, czy elementy przechowywane w kolekcji można można utworzyć zrzutu diagnostyki  
  
-   Określa, czy kolekcja jest bezpieczne  
  
 Poniższa tabela [kolekcji elementów kształtu](#_core_collection_shape_features), zawiera podsumowanie właściwości kształtów dostępne kolekcji.  
  
-   Kolumny 2 i 3 opisano każdy kształt kolejności i dostęp do właściwości. W tabeli termin "uporządkowane" oznacza, że kolejność, w której elementy są wstawiane i usunąć określa ich kolejność, w kolekcji; nie oznacza to, że elementy są sortowane według ich zawartości. Termin "indexed" oznacza, że elementy w kolekcji mogą zostać pobrane przez indeks liczba całkowita, podobnie jak elementów w tablicy typowych.  
  
-   Kolumny 4 i 5 opisują wydajności każdego kształtu. W aplikacji, które wymagają wielu wstawienia do kolekcji szybkości wstawiania może być szczególnie ważne; dla innych aplikacji szybkość wyszukiwania może być większe znaczenie.  
  
-   Kolumna 6 opisuje, czy każdy kształt umożliwia zduplikowane elementy.  
  
### <a name="_core_collection_shape_features"></a>  Kolekcja elementów kształtu  
  
|Kształt|uporządkowane|Indeksowane|Wstaw element|Wyszukiwanie określonego elementu|Zduplikowane elementy|  
|-----------|--------------|--------------|-----------------------|----------------------------------|-------------------------|  
|Lista|Tak|Nie|Szybkie|Powolne|Tak|  
|Tablica|Tak|Przez int|Powolne|Powolne|Tak|  
|mapy|Nie|Według klucza|Szybkie|Szybkie|Tak (wartości) (kluczy)|  
  
 Poniższa tabela [właściwości z kolekcji klasy MFC](#_core_characteristics_of_mfc_collection_classes), zawiera podsumowanie innych istotnych cech określonej klasy kolekcji MFC jako przewodnik do zaznaczenia. Wybór może zależeć od Określa, czy klasa jest oparte na szablonach C++, czy jego elementów może być Zserializowany za pośrednictwem dokumentu MFC [serializacji](../mfc/serialization-in-mfc.md) mechanizmu, czy jego elementy można utworzyć zrzutu za pomocą MFC na diagnostycznych zrzucanie mechanizmu, lub Określa, czy klasa jest bezpieczne, oznacza to, czy można zagwarantować typ elementów przechowywanych w i pobierane z kolekcją oparty na klasie.  
  
### <a name="_core_characteristics_of_mfc_collection_classes"></a>  Właściwości klasy kolekcji MFC  
  
|Class|Używa języka C++<br /><br /> szablony|Może być<br /><br /> serializowany|Może być<br /><br /> utworzyć zrzutu|jest<br /><br /> bezpieczne|  
|-----------|------------------------------|---------------------------|-----------------------|-----------------------|  
|`CArray`|Tak|Tak 1|Tak 1|Nie|  
|`CByteArray`|Nie|Tak|Tak|Tak 3|  
|`CDWordArray`|Nie|Tak|Tak|Tak 3|  
|`CList`|Tak|Tak 1|Tak 1|Nie|  
|`CMap`|Tak|Tak 1|Tak 1|Nie|  
|`CMapPtrToPtr`|Nie|Nie|Tak|Nie|  
|`CMapPtrToWord`|Nie|Nie|Tak|Nie|  
|`CMapStringToOb`|Nie|Tak|Tak|Nie|  
|`CMapStringToPtr`|Nie|Nie|Tak|Nie|  
|`CMapStringToString`|Nie|Tak|Tak|Tak 3|  
|`CMapWordToOb`|Nie|Tak|Tak|Nie|  
|`CMapWordToPtr`|Nie|Nie|Tak|Nie|  
|`CObArray`|Nie|Tak|Tak|Nie|  
|`CObList`|Nie|Tak|Tak|Nie|  
|`CPtrArray`|Nie|Nie|Tak|Nie|  
|`CPtrList`|Nie|Nie|Tak|Nie|  
|`CStringArray`|Nie|Tak|Tak|Tak 3|  
|`CStringList`|Nie|Tak|Tak|Tak 3|  
|`CTypedPtrArray`|Tak|Zależy od 2|Tak|Tak|  
|`CTypedPtrList`|Tak|Zależy od 2|Tak|Tak|  
|`CTypedPtrMap`|Tak|Zależy od 2|Tak|Tak|  
|`CUIntArray`|Nie|Nie|Tak|Tak 3|  
|`CWordArray`|Nie|Tak|Tak|Tak 3|  
  
 1. Do serializacji, należy jawnie wywołać obiekt kolekcji `Serialize` funkcji; aby zrzutu, należy jawnie wywołać jej `Dump` funkcji. Nie można użyć formularza `ar << collObj` do serializacji lub w formularzu `dmp` `<< collObj` do zrzutu.  
  
 2. Uszeregowieniem zależy od źródłowego typu kolekcji. Na przykład, jeśli tablica typizowaną wskaźnika jest oparta na `CObArray`, jest możliwy do serializacji; Jeśli na podstawie `CPtrArray`, nie jest możliwy do serializacji. Ogólnie rzecz biorąc nie można zserializować klasy "Ptr".  
  
 3. Po zaznaczeniu tak w tej kolumnie klasy kolekcji nieszablonu będzie bezpieczny, pod warunkiem używać zgodnie z założeniami. Na przykład, jeśli przechowujesz bajtów w `CByteArray`, tablica jest bezpieczne. Ale jeśli używasz do przechowywania znaków bezpieczeństwa jego typ jest mniej niektórych.  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcje](../mfc/collections.md)   
 [Klasy oparte na szablonach](../mfc/template-based-classes.md)   
 [Porady: tworzenie bezpiecznej kolekcji](../mfc/how-to-make-a-type-safe-collection.md)   
 [Uzyskiwanie dostępu do wszystkich składowych kolekcji](../mfc/accessing-all-members-of-a-collection.md)

