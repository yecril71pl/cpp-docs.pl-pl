---
title: Klasy kolekcji ATL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DestructElements function
- collection classes, choosing
- ConstructElements function
- SerializeElements function
- traits classes
- collection classes, about collection classes
- CTraits classes
- collection classes
ms.assetid: 4d619d46-5b4e-41dd-b9fd-e86b1fbc00b5
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8be61044a9cc6883eab74eb8093b79ea84aacc60
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="atl-collection-classes"></a>Klasy kolekcji ATL
ATL zawiera wiele klas do przechowywania i uzyskiwania dostępu do danych. Klasy, które będą używane zależy od wielu czynników, takich jak:  
  
-   Ilość danych do przechowywania  
  
-   Wydajność i wydajności podczas uzyskiwania dostępu do danych  
  
-   Możliwość dostępu do danych przez indeks lub klucz  
  
-   Uporządkowanie danych  
  
-   Osobiste preferencji  
  
## <a name="small-collection-classes"></a>Klasy kolekcji małe  
 ATL zawiera następujące klasy tablic dotyczące postępowania w przypadku małej liczby obiektów. Te klasy jest jednak ograniczona i przeznaczony do użytku wewnętrznego przez ATL. Nie zaleca się używania ich w programach.  
  
|Class|Typ magazynu danych|  
|-----------|--------------------------|  
|[CSimpleArray](../atl/reference/csimplearray-class.md)|Implementuje klasę tablicy dotyczące postępowania w przypadku małej liczby obiektów.|  
|[CSimpleMap](../atl/reference/csimplemap-class.md)|Implementuje klasę mapowania zajmujących się małej liczby obiektów.|  
  
## <a name="general-purpose-collection-classes"></a>Klasy kolekcji ogólnego przeznaczenia  
 Klasy wykonaj wdrożenie tablic, list i map i są dostępne jako ogólnego przeznaczenia klasy kolekcji:  
  
|Class|Typ magazynu danych|  
|-----------|--------------------------|  
|[CAtlArray](../atl/reference/catlarray-class.md)|Implementuje tablicy.|  
|[CAtlList](../atl/reference/catllist-class.md)|Implementuje listę.|  
|[CAtlMap](../atl/reference/catlmap-class.md)|Implementuje strukturą mapowania, według których dane mogą odwoływać się klucz lub wartość.|  
|[CRBMap](../atl/reference/crbmap-class.md)|Implementuje struktury mapowanie przy użyciu algorytmu czarne czerwony.|  
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|Implementuje strukturą multimapping czarne czerwony.|  
  
 Te klasy będą stosowane, wiele błędów programowania, gdy jest używany w kompilacjach debugowania, ale for sake of wydajności, kontrole nie zostanie wykonana w sprzedaży detalicznej kompilacji.  
  
## <a name="specialized-collection-classes"></a>Klasy kolekcji specjalne  
 Klasy kolekcji wyspecjalizowanego podawane są również zarządzania wskaźniki pamięci i wskaźniki interfejsu:  
  
|Class|Cel|  
|-----------|-------------|  
|[CAutoPtrArray](../atl/reference/cautoptrarray-class.md)|Udostępnia metody przydatne podczas konstruowania tablicę wskaźniki inteligentne.|  
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|Udostępnia metody przydatne podczas konstruowania listy wskaźniki inteligentne.|  
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|Magazyny `IUnknown` wskaźniki i jest przeznaczony do użycia jako parametr [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) klasy szablonu.|  
|[CHeapPtrList](../atl/reference/cheapptrlist-class.md)|Udostępnia metody przydatne podczas konstruowania listy wskaźniki stosu.|  
|[CInterfaceArray](../atl/reference/cinterfacearray-class.md)|Udostępnia metody przydatne podczas tworzenia tablicy wskaźników interfejsów COM..|  
|[CInterfaceList](../atl/reference/cinterfacelist-class.md)|Udostępnia metody przydatne podczas konstruowania listy wskaźników interfejsów COM..|  
  
## <a name="choosing-a-collection-class"></a>Wybieranie klasy kolekcji  
 Kolekcja dostępnych klas oferuje różne charakterystyki, jak pokazano w poniższej tabeli.  
  
-   Kolumny 2 i 3 opisano porządkowanie każdej klasy i dostęp do właściwości. W tabeli termin "uporządkowane" oznacza, że kolejność, w której elementy są wstawiane i usunąć określa ich kolejność, w kolekcji; nie oznacza to, że elementy są sortowane według ich zawartości. Termin "indexed" oznacza, że elementy w kolekcji mogą zostać pobrane przez indeks liczba całkowita, podobnie jak elementów w tablicy typowych.  
  
-   Kolumny 4 i 5 opisują wydajności każdej klasy. W aplikacji, które wymagają wielu wstawienia do kolekcji szybkości wstawiania może być szczególnie ważne; dla innych aplikacji szybkość wyszukiwania może być większe znaczenie.  
  
-   Kolumna 6 opisuje, czy każdy kształt umożliwia zduplikowane elementy.  
  
-   Relacja między czas wymagany do ukończenia operacji i liczba elementów w kolekcji wyrażonych wydajności operacji klasy danej kolekcji. Operacja trwa ilość czasu, która zwiększa liniowo opisane liczba wzrasta elementów jako algorytm O(n). Z kolei operacja trwa pewien czas, który zwiększa się mniej i mniejsza niż liczba elementów zwiększa jest nazywane algorytm O (dziennika n). W związku z tym pod względem wydajności, algorytmy O (dziennika n) przewyższyć algorytmów O(n) bardziej jako liczba wzrasta elementów.  
  
### <a name="collection-shape-features"></a>Kolekcja elementów kształtu  
  
|Kształt|uporządkowane|Indeksowane|Wstaw<br /><br /> — element|Wyszukaj<br /><br /> określony element|Zduplikowana<br /><br /> elementy|  
|-----------|--------------|--------------|---------------------------|--------------------------------------|-----------------------------|  
|Lista|Tak|Nie|Protokół Fast (czas stałe)|Powolna O(n)|Tak|  
|Tablica|Tak|Przez int (czas stałe)|Powolna O(n) z wyjątkiem wstawiania na końcu, jeśli w czasie wielkość stałej|Powolna O(n)|Tak|  
|mapy|Nie|Według klucza (czas stałe)|Protokół Fast (czas stałe)|Protokół Fast (czas stałe)|Tak (wartości) (kluczy)|  
|Czarne czerwony mapy|Tak (według kluczy)|Według klucza O (dziennika n)|Szybkie O (dziennika n)|Szybkie O (dziennika n)|Nie|  
|Multimap czarne czerwony|Tak (według kluczy)|Według klucza O(log n) (wiele wartości dla każdego klucza)|Szybkie O (dziennika n)|Szybkie O (dziennika n)|Tak (wiele wartości dla każdego klucza)|  
  
## <a name="using-ctraits-objects"></a>Przy użyciu ctraits — obiekty  
 Jako klasy kolekcji ATL mogą być używane do przechowywania szeroką gamę typy danych zdefiniowane przez użytkownika, może być przydatne można było zastąpić ważne funkcje, takie jak porównania. Jest to osiągane przy użyciu ctraits — klasy.  
  
 Ctraits — klasy są podobne do, ale bardziej elastyczne niż funkcje pomocnicze klasy kolekcji MFC; zobacz [pomocnicy klasy kolekcji](../mfc/reference/collection-class-helpers.md) Aby uzyskać więcej informacji.  
  
 Podczas tworzenia klasy kolekcji, masz możliwość określenia ctraits — klasy. Ta klasa będzie zawierać kod, który będzie wykonywać operacji, takich jak porównania wywołanego metody wchodzące w skład klasie kolekcji. Na przykład obiekt listy zawiera własne struktury zdefiniowane przez użytkownika, można ponownie zdefiniować testu równości można porównywać tylko niektóre zmienne Członkowskie. W ten sposób metody Find obiekt listy będzie działać w sposób bardziej użyteczne.  
  
## <a name="example"></a>Przykład  
  
### <a name="code"></a>Kod  
 [!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/cpp/atl-collection-classes_1.cpp)]  
  
## <a name="comments"></a>Komentarze  
 Aby uzyskać listę ctraits — klasy, zobacz [klasy kolekcji](../atl/collection-classes.md).  
  
 Na poniższym diagramie przedstawiono hierarchii klas dla ctraits — klasy.  
  
 ![Hierarchia cech dla klasy kolekcji](../atl/media/vctraitscollectionclasseshierarchy.gif "vctraitscollectionclasseshierarchy")  
  
## <a name="collection-classes-samples"></a>Przykłady klasy kolekcji  
 Poniższe przykłady pokazują klasy kolekcji:  
  
-   [Przykładowe MMXSwarm](../visual-cpp-samples.md)  
  
-   [Przykładowe DynamicConsumer](../visual-cpp-samples.md)  
  
-   [Przykładowe UpdatePV](../visual-cpp-samples.md)  
  
-   [Przykładowe ramki](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../atl/active-template-library-atl-concepts.md)   
 [Klasy kolekcji](../atl/collection-classes.md)

