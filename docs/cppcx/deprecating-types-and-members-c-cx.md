---
title: Przestarzałe typy i składoweC++(/CX)
ms.date: 12/30/2016
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
ms.openlocfilehash: 6cd880af7e206b4c7338e53615594ec2c65c59fc
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740499"
---
# <a name="deprecating-types-and-members-ccx"></a>Przestarzałe typy i składoweC++(/CX)

W C++programie/CX jest możliwe wycofanie typów środowisko wykonawcze systemu Windows i członków dla producentów i konsumentów przy użyciu [przestarzałego](/uwp/api/windows.foundation.metadata.deprecatedattribute) atrybutu. Jeśli korzystasz z interfejsu API, do którego zastosowano ten atrybut, otrzymasz komunikat ostrzegawczy czasu kompilacji, który wskazuje, że interfejs API jest przestarzały, a także zaleca alternatywny interfejs API do użycia. We własnych typach i metodach publicznych można zastosować ten atrybut i podać własny komunikat niestandardowy.

> [!CAUTION]
> [Przestarzały](/uwp/api/windows.foundation.metadata.deprecatedattribute) atrybut jest używany tylko z typami środowisko wykonawcze systemu Windows. Dla standardowych C++ klas i elementów członkowskich Użyj [__declspec (przestarzałe)](../cpp/deprecated-cpp.md).

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zastąpić własne publiczne interfejsy API — na przykład w składniku środowisko wykonawcze systemu Windows. Drugi parametr typu [Windows: Foundation:: Metadata::D eprecationtype](/uwp/api/windows.foundation.metadata.deprecationtype) określa, czy interfejs API jest przestarzały czy usunięty. Obecnie obsługiwana jest tylko wartość DeprecationType::D eprecated. Trzeci parametr w atrybucie określa [Windows:: Foundation:: Metadata::P latform](/uwp/api/windows.foundation.metadata.platformattribute) , do którego odnosi się ten atrybut.

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

## <a name="supported-targets"></a>Obsługiwane elementy docelowe

W poniższej tabeli wymieniono konstrukcje, do których można zastosować przestarzały atrybut:

| |
|-|
|Kontrolka XAML|
|delegate|
|zdarzenie|
|pole wyliczeniowe|
|enum|
|struktura|
|— metoda|
|class|
|interface|
|property|
|pole struktury|
|sparametryzowany Konstruktor|

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
