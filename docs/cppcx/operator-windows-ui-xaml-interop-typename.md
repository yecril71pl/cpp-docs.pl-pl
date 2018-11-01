---
title: operator Windows::UI::Xaml::Interop::TypeName
ms.date: 12/30/2016
ms.assetid: a65a105e-7e3a-452f-932f-2cdaf00fbba5
ms.openlocfilehash: c77655ed7692c4cdccc311bc27c492126d62e54e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659217"
---
# <a name="operator-windowsuixamlinteroptypename"></a>operator Windows::UI::Xaml::Interop::TypeName

Umożliwia konwersję z `Platform::Type` do [Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx).

## <a name="syntax"></a>Składnia

```cpp
Operator TypeName(Platform::Type^ type);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca [Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) danego pseudoelementu `Platform::Type^`.

### <a name="remarks"></a>Uwagi

`TypeName` jest niezależny od języka struktura Windows Runtime reprezentujących informacje o typie. [Platform::type](../cppcx/platform-type-class.md) jest specyficzne dla języka C++ i nie mogą być przekazywane między interfejsem binarnym aplikacji (ABI). W tym miejscu jest jednym z zastosowań `TypeName`w [Navigate](https://msdn.microsoft.com/library/windows/apps/hh702394.aspx) funkcji:

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

### <a name="example"></a>Przykład

W kolejnym przykładzie pokazano, jak przeprowadzać konwersję między `TypeName` i `Type`.

```

// Convert from Type to TypeName
Windows::UI::Xaml::Interop::TypeName tn = TypeName(MainPage::typeid);

// Convert back from TypeName to Type
Type^ tx2 = (Type^)(tn);
```

## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework

Projekt programy .NET framework `TypeName` jako [System.Type](assetId:///System.Type?qualifyHint=False&autoUpgrade=True).

### <a name="requirements"></a>Wymagania

## <a name="see-also"></a>Zobacz też

[Operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)<br/>
[Platform::Type, klasa](../cppcx/platform-type-class.md)