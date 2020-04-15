---
title: operator Windows::UI::Xaml::Interop::TypeName
ms.date: 12/30/2016
ms.assetid: a65a105e-7e3a-452f-932f-2cdaf00fbba5
ms.openlocfilehash: d35056ca1a4e7f06c9f91fe86998a676a12395f2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336998"
---
# <a name="operator-windowsuixamlinteroptypename"></a>operator Windows::UI::Xaml::Interop::TypeName

Umożliwia konwersję z `Platform::Type` systemu [Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename).

## <a name="syntax"></a>Składnia

```cpp
Operator TypeName(Platform::Type^ type);
```

### <a name="return-value"></a>Wartość zwracana

Zwraca [system Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename) `Platform::Type^`po podaniu .

### <a name="remarks"></a>Uwagi

`TypeName`jest neutralną dla języka strukturą środowiska wykonawczego systemu Windows do reprezentowania informacji o typie. [Platforma::Type](../cppcx/platform-type-class.md) jest specyficzne dla języka C++ i nie można przekazać przez interfejs binarny aplikacji (ABI). Oto jedno użycie `TypeName`, w [funkcji Nawigacja:](/uwp/api/windows.ui.xaml.controls.frame.navigate)

```cpp
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

### <a name="example"></a>Przykład

W następnym przykładzie pokazano, jak przekonwertować między programem `TypeName` . `Type`

```cpp
// Convert from Type to TypeName
Windows::UI::Xaml::Interop::TypeName tn = TypeName(MainPage::typeid);

// Convert back from TypeName to Type
Type^ tx2 = (Type^)(tn);
```

## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework

Programy platformy .NET `TypeName` Framework są projektami jako [System.Type](/dotnet/api/system.type).

### <a name="requirements"></a>Wymagania

## <a name="see-also"></a>Zobacz też

[operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)<br/>
[Platform::Type, klasa](../cppcx/platform-type-class.md)
