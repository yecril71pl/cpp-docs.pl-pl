---
title: Platforma::Obszar nazw kolekcji
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- collection/Platform::Collections
helpviewer_keywords:
- Platform::Collections Namespace
ms.assetid: b5042864-5f22-40b7-b7a5-c0691f65cc47
ms.openlocfilehash: ab6b78f1b88c586a11276d36387fb42ea6ee667f
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032424"
---
# <a name="platformcollections-namespace"></a>Platforma::Obszar nazw kolekcji

Obszar nazw Platformy::Kolekcje `Map`zawiera `MapView` `Vector`, `VectorView` , i klasy. Te klasy są konkretne implementacje odpowiednich interfejsów, które są zdefiniowane w [windows::Foundation::Collections](/uwp/api/windows.foundation.collections) przestrzeni nazw. Typy kolekcji betonu nie są przenośne w środowisku ABI (na przykład, gdy program Javascript lub C# wywołuje składnik C++), ale są niejawnie konwertowane na odpowiednie typy interfejsów. Na przykład jeśli zaimplementujesz metodę publiczną, która wypełnia i zwraca kolekcję, a następnie użyj [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) do zaimplementowania kolekcji wewnętrznie i użyj [windows::Foundation::Collections::IVector](/uwp/api/windows.foundation.collections.ivector-1) jako typu zwracanego. Aby uzyskać więcej informacji, zobacz [Kolekcje](../cppcx/collections-c-cx.md) i [tworzenie składników środowiska wykonawczego systemu Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

Można utworzyć platformę::Collections::Vector z [std::vector](../standard-library/vector-class.md) i [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) z [std::map](../standard-library/map-class.md).

Ponadto platforma::Obszar nazw kolekcji zapewnia obsługę wstecznych iteratorów `Vector` wstawiania i wprowadzania oraz iteratorów. `VectorView`

Aby używać`#include`typów w obszarze nazw Platform::Collections, należy dołączyć ( ) nagłówek collection.h.

## <a name="syntax"></a>Składnia

```cpp
#include <collection.h>
using namespace Platform::Collections;
```

### <a name="members"></a>Elementy członkowskie

Ta przestrzeń nazw zawiera następujące elementy członkowskie.

|Nazwa|Opis|
|----------|-----------------|
|[Platforma::Kolekcje::Klasa BackInsertIterator](../cppcx/platform-collections-backinsertiterator-class.md)|Reprezentuje iteratora, który wstawia element na końcu kolekcji.|
|[Platform::Collections::InputIterator, klasa](../cppcx/platform-collections-inputiterator-class.md)|Reprezentuje iteratora, który wstawia element na początku kolekcji.|
|[Platform::Collections::Map, klasa](../cppcx/platform-collections-map-class.md)|Reprezentuje modyfikowalną kolekcję par klucz-wartość, które są dostępne przez klucz. Podobne do [std::map](../standard-library/map-class.md).|
|[Platform::Collections::MapView, klasa](../cppcx/platform-collections-mapview-class.md)|Reprezentuje kolekcję tylko do odczytu par klucza wartości, które są dostępne przez klucz.|
|[Platform::Collections::Vector, klasa](../cppcx/platform-collections-vector-class.md)|Reprezentuje modyfikowalną sekwencję elementów. Podobne do [std::vector](../standard-library/vector-class.md).|
|[Platform::Collections::VectorIterator, klasa](../cppcx/platform-collections-vectoriterator-class.md)|Reprezentuje iteratora, który `Vector` przechodzi przez kolekcję.|
|[Platform::Collections::VectorView, klasa](../cppcx/platform-collections-vectorview-class.md)|Reprezentuje sekwencję tylko do odczytu elementów.|
|[Platform::Collections::VectorViewIterator, klasa](../cppcx/platform-collections-vectorviewiterator-class.md)|Reprezentuje iteratora, który `VectorView` przechodzi przez kolekcję.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)

### <a name="requirements"></a>Wymagania

**Metadane:** platform.winmd

**Obszar nazw:** Platforma::Kolekcje

**Opcja kompilatora:** /ZW

## <a name="see-also"></a>Zobacz też

[Obszar nazw platformy](../cppcx/platform-namespace-c-cx.md)
