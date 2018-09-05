---
title: Typ operatora ^ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: b24ffc83-0780-4f9a-8ee0-f5725db339d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8abccf48219b70040ce728ba0dff9fa02b57bfc0
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688468"
---
# <a name="operator-type"></a>operator Type^
Umożliwia konwersję z [Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) do `Platform::Type`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
Operator Type^(Windows::UI::Xaml::Interop::TypeName typeName)  
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
 [Operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)   
 [Platform::Type, klasa](../cppcx/platform-type-class.md)