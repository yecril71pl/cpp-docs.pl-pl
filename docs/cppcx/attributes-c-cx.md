---
title: Atrybuty (C++/CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: 5f74914ab65fdf2c1803b47665e16378991efa3c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209458"
---
# <a name="attributes-ccx"></a>Atrybuty (C++/CX)

Atrybut jest specjalnym rodzajem klasy referencyjnej, która może zostać dołączony w nawiasach kwadratowych do typów środowiska wykonawczego Windows i metod, aby określić niektóre zachowania podczas tworzenia metadanych. Kilka wstępnie zdefiniowanych atrybutów — na przykład [Windows::Foundation::Metadata::WebHostHidden](/uwp/api/Windows.Foundation.Metadata.WebHostHiddenAttribute)— są często używane w C++/CX kodu. Ten przykład pokazuje, jak ten atrybut jest stosowany do klasy:

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

## <a name="see-also"></a>Zobacz także

[System typów (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
