---
title: Atrybuty (C + +/ CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: 13a2639a877d1ba926d74511addcf72763967d85
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462247"
---
# <a name="attributes-ccx"></a>Atrybuty (C + +/ CX)

Atrybut jest specjalnym rodzajem klasy referencyjnej, która może zostać dołączony w nawiasach kwadratowych do typów środowiska wykonawczego Windows i metod, aby określić niektóre zachowania podczas tworzenia metadanych. Kilka wstępnie zdefiniowanych atrybutów — na przykład [Windows::Foundation::Metadata::WebHostHidden](https://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.webhosthiddenattribute.aspx)— są często używane w języku C + +/ CX kodu. Ten przykład pokazuje, jak ten atrybut jest stosowany do klasy:

[!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]

## <a name="custom-attributes"></a>Atrybuty niestandardowe

Można również zdefiniować atrybutów niestandardowych. Atrybutów niestandardowych, które muszą spełniać te reguły Windows Runtime:

- Atrybutów niestandardowych, które mogą zawierać tylko pola publiczne.

- Pola atrybutu niestandardowego może być inicjowana, gdy jest stosowany do klasy.

- Pole może być jednego z następujących typów:

   - Int32 (int)

   - UInt32 (unsigned int)

   - bool

   - Platform::String ^

   - Windows::Foundation::HResult

   - Platform::type ^

   - Klasa publicznym typie wyliczeniowym (z uwzględnieniem wyliczenia zdefiniowanych przez użytkownika)

Następny przykład pokazuje, jak zdefiniować niestandardowy atrybut i następnie zainicjowanie jej, gdy jest używany.

[!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]

## <a name="see-also"></a>Zobacz też

[System typów (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)