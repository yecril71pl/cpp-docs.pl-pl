---
title: operator Type^
ms.date: 12/30/2016
ms.assetid: b24ffc83-0780-4f9a-8ee0-f5725db339d1
ms.openlocfilehash: 5b2c0b83533af62aa96fdc4b53f5762c6ca748a4
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422172"
---
# <a name="operator-type"></a>operator Type^

Umożliwia konwersję z [Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename) do `Platform::Type`.

## <a name="syntax"></a>Składnia

```cpp
Operator Type^(Windows::UI::Xaml::Interop::TypeName typeName);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca `Platform::Type` danego pseudoelementu [Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename).

### <a name="remarks"></a>Uwagi

`TypeName` jest niezależny od języka struktura Windows Runtime reprezentujących informacje o typie. [Platform::type](../cppcx/platform-type-class.md) jest specyficzne dla języka C++ i nie mogą być przekazywane między interfejsem binarnym aplikacji (ABI). W tym miejscu jest jednym z zastosowań `TypeName`w [Navigate](/uwp/api/windows.ui.xaml.controls.frame.navigate) funkcji:

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

### <a name="example"></a>Przykład

W kolejnym przykładzie pokazano, jak przeprowadzać konwersję między `TypeName` i `Type`.

```

// Convert from Type to TypeName
TypeName tn = TypeName(MainPage::typeid);

// Convert back from TypeName to Type
Type^ tx2 = (Type^)(tn);
```

## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework

Projekt programy .NET framework `TypeName` jako <xref:System.Type>

### <a name="requirements"></a>Wymagania

## <a name="see-also"></a>Zobacz też

[Operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)<br/>
[Platform::Type, klasa](../cppcx/platform-type-class.md)