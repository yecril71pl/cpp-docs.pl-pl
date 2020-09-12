---
title: Wycofane typy i składowe (C++/CX)
ms.date: 12/30/2016
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
ms.openlocfilehash: 6d61b00690cc087c3baced6d96d0b6c8d73b5850
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040330"
---
# <a name="deprecating-types-and-members-ccx"></a>Wycofane typy i składowe (C++/CX)

W języku C++/CX jest możliwe wycofanie typów środowisko wykonawcze systemu Windows i członków dla producentów i konsumentów przy użyciu [przestarzałego](/uwp/api/windows.foundation.metadata.deprecatedattribute) atrybutu. Jeśli korzystasz z interfejsu API, do którego zastosowano ten atrybut, otrzymasz komunikat ostrzegawczy czasu kompilacji, który wskazuje, że interfejs API jest przestarzały, a także zaleca alternatywny interfejs API do użycia. We własnych typach i metodach publicznych można zastosować ten atrybut i podać własny komunikat niestandardowy.

> [!CAUTION]
> [Przestarzały](/uwp/api/windows.foundation.metadata.deprecatedattribute) atrybut jest używany tylko z typami środowisko wykonawcze systemu Windows. W przypadku standardowych klas i elementów członkowskich języka C++ Użyj [__declspec (przestarzałe)](../cpp/deprecated-cpp.md).

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

:::row:::
   :::column span="":::
      określonej
      Wierz
      podstawowe
      pole wyliczeniowe \
      wydarzen
      interface
   :::column-end:::
   :::column span="":::
      Method
      sparametryzowany Konstruktor \
      wartość
      konstrukcja
      pole struktury \
      Kontrolka XAML
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Zobacz także

[System typów](../cppcx/type-system-c-cx.md)<br/>
[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Dokumentacja przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)
