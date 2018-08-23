---
title: Platform::Collections Namespace | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2018
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- collection/Platform::Collections
dev_langs:
- C++
helpviewer_keywords:
- Platform::Collections Namespace
ms.assetid: b5042864-5f22-40b7-b7a5-c0691f65cc47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 171fdfe8e174d0d3b5d1c69e9aa5a777a3148ee0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612534"
---
# <a name="platformcollections-namespace"></a>Platform::Collections Namespace

Platform::Collections, przestrzeń nazw zawiera `Map`, `MapView`, `Vector`, i `VectorView` klasy. Te klasy są konkretnych implementacji odpowiednich interfejsów, które są zdefiniowane w [Windows::Foundation:: Collections](http://go.microsoft.com/fwlink/p/?LinkId=262645) przestrzeni nazw. Typy kolekcji konkretnych nie są przenośne między ABI (na przykład gdy Javascript lub C# program wywołania do składnika C++), ale są one niejawnie konwertowany jako odpowiednie typy interfejsu. Na przykład, jeśli należy zaimplementować metodę publiczną, która wypełnia i zwraca kolekcję, użyj [platform::Collections:: Vector](../cppcx/platform-collections-vector-class.md) wewnętrznie implementacji zbierania i używania [Windows::Foundation:: Collections: : IVector](http://go.microsoft.com/fwlink/p/?LinkId=262410) jako typ zwracany. Aby uzyskać więcej informacji, zobacz [kolekcje](../cppcx/collections-c-cx.md) i [Tworzenie składników środowiska wykonawczego Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

Platform::Collections:: Vector z można skonstruować [std::vector](../standard-library/vector-class.md) i [platform::Collections:: map](../cppcx/platform-collections-map-class.md) z [std::map](../standard-library/map-class.md).

Ponadto Platform::Collections, przestrzeń nazw zapewnia obsługę wstawiania wstecz i Iteratory danych wejściowych i `Vector` i `VectorView` Iteratory.

Musi zawierać (`#include`) nagłówka collection.h na używanie typów w Platform::Collections, przestrzeń nazw.

## <a name="syntax"></a>Składnia

```cpp
#include <collection.h>
using namespace Platform::Collections;
```

### <a name="members"></a>Elementy członkowskie

Ta przestrzeń nazw zawiera następujące elementy członkowskie.

|Nazwa|Opis|
|----------|-----------------|
|[Platform::Collections::BackInsertIterator, klasa](../cppcx/platform-collections-backinsertiterator-class.md)|Reprezentuje iterator, który wstawia element na końcu kolekcji.|
|[Platform::Collections::InputIterator, klasa](../cppcx/platform-collections-inputiterator-class.md)|Reprezentuje iterator, który wstawia element na początku kolekcji.|
|[Platform::Collections::Map, klasa](../cppcx/platform-collections-map-class.md)|Reprezentuje kolekcję można modyfikować pary klucz wartość, które są dostępne przy użyciu klucza. Podobnie jak [std::map](../standard-library/map-class.md).|
|[Platform::Collections::MapView, klasa](../cppcx/platform-collections-mapview-class.md)|Reprezentuje kolekcję par klucz wartość, które są dostępne przy użyciu klucza tylko do odczytu.|
|[Platform::Collections::Vector, klasa](../cppcx/platform-collections-vector-class.md)|Reprezentuje sekwencję można modyfikować elementów. Podobnie jak [std::vector](../standard-library/vector-class.md).|
|[Platform::Collections::VectorIterator, klasa](../cppcx/platform-collections-vectoriterator-class.md)|Reprezentuje iterator, który przechodzi przez `Vector` kolekcji.|
|[Platform::Collections::VectorView, klasa](../cppcx/platform-collections-vectorview-class.md)|Reprezentuje atrybut tylko do odczytu sekwencję elementów.|
|[Platform::Collections::VectorViewIterator, klasa](../cppcx/platform-collections-vectorviewiterator-class.md)|Reprezentuje iterator, który przechodzi przez `VectorView` kolekcji.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)

### <a name="requirements"></a>Wymagania

**Metadane:** platform.winmd

**Namespace:** Platform::Collections

**— Opcja kompilatora:** /ZW

## <a name="see-also"></a>Zobacz także

[Namespace platformy](../cppcx/platform-namespace-c-cx.md)  
