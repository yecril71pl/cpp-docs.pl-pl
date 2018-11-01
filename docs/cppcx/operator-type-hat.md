---
title: operator Type^
ms.date: 12/30/2016
ms.assetid: b24ffc83-0780-4f9a-8ee0-f5725db339d1
ms.openlocfilehash: fca53abb9dc17588695591d496b7db2a76e319f6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553663"
---
# <a name="operator-type"></a>operator Type^

Umożliwia konwersję z [Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) do `Platform::Type`.

## <a name="syntax"></a>Składnia

```cpp
Operator Type^(Windows::UI::Xaml::Interop::TypeName typeName);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca `Platform::Type` danego pseudoelementu [Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx).

### <a name="remarks"></a>Uwagi

`TypeName` jest niezależny od języka struktura Windows Runtime reprezentujących informacje o typie. [Platform::type](../cppcx/platform-type-class.md) jest specyficzne dla języka C++ i nie mogą być przekazywane między interfejsem binarnym aplikacji (ABI). W tym miejscu jest jednym z zastosowań `TypeName`w [Navigate](https://msdn.microsoft.com/library/windows/apps/hh702394.aspx) funkcji:

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