---
title: operator typu ^ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: b24ffc83-0780-4f9a-8ee0-f5725db339d1
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aef888e6c9e22c361f54674aaef420531e75630b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="operator-type"></a>operator Type^
Konwersja z umożliwia [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) do `Platform::Type`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
Operator Type^(Windows::UI::Xaml::Interop::TypeName typeName)  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `Platform::Type` , gdy [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx).  
  
### <a name="remarks"></a>Uwagi  
 `TypeName` jest niezależny od języka struktura środowiska wykonawczego systemu Windows reprezentująca informacji o typie. [Platform::type](../cppcx/platform-type-class.md) są specyficzne dla języka C++ i nie mogą być przekazywane przez interfejs binarne aplikacji (ABI). W tym miejscu stanowi jedno użycie `TypeName`w [Nawigacja](http://msdn.microsoft.com/library/windows/apps/hh702394.aspx) funkcji:  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
### <a name="example"></a>Przykład  
 W kolejnym przykładzie pokazano sposób konwertowania między `TypeName` i `Type`.  
  
```  
  
// Convert from Type to TypeName  
TypeName tn = TypeName(MainPage::typeid);  
  
// Convert back from TypeName to Type  
Type^ tx2 = (Type^)(tn);  
  
```  
  
## <a name="net-framework-equivalent"></a>Odpowiednik w programie .NET Framework  
 Projekt programy .NET framework `TypeName` jako [System.Type](assetId:///System.Type?qualifyHint=False&autoUpgrade=True).  
  
### <a name="requirements"></a>Wymagania  
  
## <a name="see-also"></a>Zobacz też  
 [Operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-subtractwindows-ui-xaml-interop-typename.md)   
 [Platform::Type, klasa](../cppcx/platform-type-class.md)