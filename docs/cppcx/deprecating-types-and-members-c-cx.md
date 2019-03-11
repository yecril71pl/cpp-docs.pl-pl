---
title: Wycofane typy i składowe (C + +/ CX)
ms.date: 12/30/2016
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
ms.openlocfilehash: 7f488dfa522c0b48c75150d40584b0946baae806
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748453"
---
# <a name="deprecating-types-and-members-ccx"></a>Wycofane typy i składowe (C + +/ CX)

W języku C + +/ CX, amortyzacja typów środowiska wykonawczego Windows i elementów członkowskich dla producentów i konsumentów, za pomocą [uznane za przestarzałe](/uwp/api/windows.foundation.metadata.deprecatedattribute) atrybut jest obsługiwany. Jeśli wykorzystasz interfejsu API, do którego zastosowano ten atrybut, otrzymasz komunikat ostrzegawczy kompilacji, która wskazuje, że interfejs API jest przestarzały i zaleca również alternatywny interfejsu API do użycia. We własnych typów publicznych i metody można zastosować ten atrybut i Podaj własny niestandardowy komunikat.

> [!CAUTION]
> [Uznane za przestarzałe](/uwp/api/windows.foundation.metadata.deprecatedattribute) atrybut jest tylko do użytku z typami środowiska wykonawczego Windows. W przypadku standardowych klas C++ i elementów członkowskich, użyj [__declspec(deprecated)](../cpp/deprecated-cpp.md).

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak wycofana własnych publicznych interfejsów API — na przykład w składnika wykonawczego Windows. Drugi parametr typu [Windows: Foundation:: Metadata::DeprecationType](/uwp/api/windows.foundation.metadata.deprecationtype) Określa, czy interfejs API jest przestarzała lub usunięta. Obecnie tylko DeprecationType::Deprecated wartość jest obsługiwana. Określa trzeci parametr w atrybucie [Windows::Foundation::Metadata::Platform](/uwp/api/windows.foundation.metadata.platformattribute) którego dotyczy ten atrybut.

```

namespace wfm = Windows::Foundation::Metadata;

public ref class Bicycle sealed
{

public:
    property double Speed;

    [wfm::Deprecated("Use the Speed property to compute the angular speed of the wheel", wfm::DeprecationType::Deprecate, 0x0)]
    double ComputeAngularVelocity();
};
```

## <a name="supported-targets"></a>Obsługiwane obiekty docelowe

W poniższej tabeli wymieniono konstrukcje, których można zastosować atrybutu uznane za przestarzałe:

| |
|-|
|Kontrolki XAML|
|delegate|
|zdarzenie|
|pola wyliczenia|
|enum|
|struktura |
|— metoda|
|class|
|interface|
|property|
|pole — struktura|
|Konstruktor sparametryzowany|

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
