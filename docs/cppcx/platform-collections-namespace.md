---
title: Platform::Collections Namespace | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/25/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: collection/Platform::Collections
dev_langs: C++
helpviewer_keywords: Platform::Collections Namespace
ms.assetid: b5042864-5f22-40b7-b7a5-c0691f65cc47
caps.latest.revision: "9"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a93282a233f98d7a384d1fdad2ba6ca862e9e3f2
ms.sourcegitcommit: c2e990450ccd528d85b2783fbc63042612987cfd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2018
---
# <a name="platformcollections-namespace"></a>Platform::Collections Namespace
Przestrzeń nazw Platform::Collections zawiera `Map`, `MapView`, `Vector`, i `VectorView` klasy. Te klasy są konkretnych implementacje odpowiednie interfejsy, które są zdefiniowane w [Windows::Foundation::Collections](http://go.microsoft.com/fwlink/p/?LinkId=262645) przestrzeni nazw. Typy kolekcji konkretnych nie są przenośny między ABI (na przykład gdy Javascript lub program wywołuje składnik C++ C#), ale są one niejawnego jako odpowiednie typy interfejsu. Na przykład, jeśli należy zaimplementować metodę publiczną, która wypełnia i zwraca kolekcję, użyj [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) do zaimplementowania wewnętrznie zbierania i użycia [Windows::Foundation::Collections: : IVector](http://go.microsoft.com/fwlink/p/?LinkId=262410) jako typ zwracany. Aby uzyskać więcej informacji, zobacz [kolekcje](../cppcx/collections-c-cx.md) i [tworzenia składników środowiska wykonawczego systemu Windows w języku C++](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md).  
  
 Można utworzyć Platform::Collections::Vector z [std::vector](../standard-library/vector-class.md) i [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) z [std::map](../standard-library/map-class.md).  
  
 Ponadto Platform::Collections przestrzeń nazw zapewnia obsługę insert Wstecz i wejściowych Iteratory i `Vector` i `VectorView` Iteratory.  
  
 Należy uwzględnić (`#include`) Użyj typów w przestrzeni nazw Platform::Collections nagłówek collection.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
  
#include <collection.h>  
using namespace Platform::Collections;  
```  
  
### <a name="members"></a>Elementy członkowskie  
 Ta przestrzeń nazw zawiera następujące elementy członkowskie.  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Platform::Collections::BackInsertIterator, klasa](../cppcx/platform-collections-backinsertiterator-class.md)|Reprezentuje iterację wstawia element na końcu kolekcji.|  
|[Platform::Collections::InputIterator, klasa](../cppcx/platform-collections-inputiterator-class.md)|Reprezentuje iterację wstawia element na początku kolekcji.|  
|[Platform::Collections::Map, klasa](../cppcx/platform-collections-map-class.md)|Reprezentuje modyfikowalną kolekcję par klucz wartość, które są dostępne przy użyciu klucza. Podobnie jak [std::map](../standard-library/map-class.md).|  
|[Platform::Collections::MapView, klasa](../cppcx/platform-collections-mapview-class.md)|Reprezentuje kolekcję par klucz wartość, które są dostępne przy użyciu klucza tylko do odczytu.|  
|[Platform::Collections::Vector, klasa](../cppcx/platform-collections-vector-class.md)|Reprezentuje sekwencję można modyfikować elementów. Podobnie jak [std::vector](../standard-library/vector-class.md).|  
|[Platform::Collections::VectorIterator, klasa](../cppcx/platform-collections-vectoriterator-class.md)|Reprezentuje iterację, który przechodzi przez `Vector` kolekcji.|  
|[Platform::Collections::VectorView, klasa](../cppcx/platform-collections-vectorview-class.md)|Reprezentuje tylko do odczytu sekwencję elementów.|  
|[Platform::Collections::VectorViewIterator, klasa](../cppcx/platform-collections-vectorviewiterator-class.md)|Reprezentuje iterację, który przechodzi przez `VectorView` kolekcji.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)  
  
### <a name="requirements"></a>Wymagania  
 **Metadane:** platform.winmd  
  
 **Namespace:** Platform::Collections  
  
 **— Opcja kompilatora:** /ZW  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace platformy](../cppcx/platform-namespace-c-cx.md)
