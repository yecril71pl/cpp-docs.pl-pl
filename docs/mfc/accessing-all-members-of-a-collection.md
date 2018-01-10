---
title: "Uzyskiwanie dostępu do wszystkich elementów członkowskich kolekcji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, collections
- enumerations [MFC]
- enumerating collections [MFC]
- collections [MFC], accessing
- collection classes [MFC]
- ', '
- ', '
- ', '
- ', '
- ', '
- ', '
- ', '
ms.assetid: 7bbae518-062e-4393-81f9-b22abd2e5f59
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 34ba2795c12695702b2e38034081e17d69c156d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="accessing-all-members-of-a-collection"></a>Uzyskiwanie dostępu do wszystkich elementów członkowskich kolekcji
Klasy kolekcji tablic MFC — zarówno na podstawie szablonu, a nie — umożliwia dostęp do swoich elementów indeksów. Klasy kolekcji listy, a następnie mapować MFC — zarówno na podstawie szablonu i nie — użyj wskaźnika typu **pozycji** do opisywania określonej pozycji w kolekcji. Aby uzyskać dostęp do co najmniej jeden członkowie tych kolekcji, należy najpierw zainicjować wskaźnik położenia wielokrotnie przekazania tej pozycji do kolekcji i poproś go do zwrócenia następnego elementu. Kolekcja nie jest odpowiedzialny za konserwację stanu informacje postępie iteracji. Czy informacje są przechowywane w wskaźnik położenia. Jednak podane określonej pozycji, Kolekcja jest odpowiedzialny za zwrócenie następnego elementu.  
  
 Poniższe procedury pokazują, jak wykonać iterację trzy rodzaje kolekcje dostarczane z MFC:  
  
-   [Iteracja tablicy](#_core_to_iterate_an_array)  
  
-   [Iteracja listy](#_core_to_iterate_a_list)  
  
-   [Iteracja mapy](#_core_to_iterate_a_map)  
  
### <a name="_core_to_iterate_an_array"></a>Do wykonywania iteracji tablicy  
  
1.  Użyj sekwencyjne numery indeksu z `GetAt` funkcji członkowskiej:  
  
     [!code-cpp[NVC_MFCCollections#12](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_1.cpp)]  
  
     W tym przykładzie użyto tablicy typizowaną wskaźnika, które zawierają wskaźniki do `CPerson` obiektów. Tablica jest pochodną klasy `CObArray`, jeden z nieszablonu wstępnie zdefiniowanych klas. `GetAt`Zwraca wskaźnik do `CPerson` obiektu. Do klasy kolekcji typizowaną wskaźnika — tablice lub list — pierwszy parametr określa klasę podstawową; drugi parametr określa typ do przechowywania.  
  
     `CTypedPtrArray` Klasy także przeciążenia **[** operator tak, aby można było używać zwyczajowe składni indeks dolny tablicy do dostępu do elementów tablicy. Zamiast instrukcji w treści `for` pętla powyżej  
  
     [!code-cpp[NVC_MFCCollections#13](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_2.cpp)]  
  
     Ten operator istnieje zarówno w **const** i nie-**const** wersji. **Const** wersji, który jest wywoływany dla **const** tablic, może się pojawić tylko po prawej stronie instrukcji przypisania.  
  
### <a name="_core_to_iterate_a_list"></a>Aby przejść do listy  
  
1.  Użyj funkcji Członkowskich `GetHeadPosition` i `GetNext` do sposobu pracy użytkownika za pośrednictwem listy:  
  
     [!code-cpp[NVC_MFCCollections#14](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_3.cpp)]  
  
     W tym przykładzie używane listy typizowaną wskaźnika do zawierają wskaźniki do `CPerson` obiektów. Deklaracja listy podobny dla tablicy w procedurze [iteracyjne tablicy](#_core_to_iterate_an_array) , ale jest pochodną klasy `CObList`. `GetNext`Zwraca wskaźnik do `CPerson` obiektu.  
  
### <a name="_core_to_iterate_a_map"></a>Do wykonywania iteracji mapy  
  
1.  Użyj `GetStartPosition` na uzyskanie dostępu do początku mapy i `GetNextAssoc` uzyskanie wielokrotnie dalej kluczy i wartości z mapy, jak pokazano na poniższym przykładzie:  
  
     [!code-cpp[NVC_MFCCollections#15](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_4.cpp)]  
  
     W tym przykładzie użyto szablonu mapy proste (zamiast kolekcji typizowaną wskaźnika), która używa `CString` kluczy i przechowuje wskaźniki do `CPerson` obiektów. Jeśli używasz funkcji dostępu, takich jak `GetNextAssoc`, ta klasa dostarcza wskaźniki do `CPerson` obiektów. Jeśli możesz użyć jednej z kolekcji mapy nieszablonu, należy rzutować zwróconego `CObject` wskaźnik na wskaźnik do `CPerson`.  
  
    > [!NOTE]
    >  W przypadku map nieszablonu kompilatora wymaga odwołania do `CObject` wskaźnika w ostatnim parametrze do `GetNextAssoc`. W danych wejściowych należy rzutować wskaźniki dla tego typu, jak pokazano w następnym przykładzie.  
  
     Szablon rozwiązania jest prostsze i zapewnia lepsze bezpieczeństwo typów. Kod nieszablonu jest bardziej skomplikowany, jak widać w tym miejscu:  
  
     [!code-cpp[NVC_MFCCollections#16](../mfc/codesnippet/cpp/accessing-all-members-of-a-collection_5.cpp)]  
  
 Aby uzyskać więcej informacji, zobacz [usuwanie wszystkich obiektów z kolekcji CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcje](../mfc/collections.md)

