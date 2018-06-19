---
title: Operator Windows::UI::Xaml::Interop::TypeName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: a65a105e-7e3a-452f-932f-2cdaf00fbba5
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 714d39a70b19998a5daddceadc2c91df65312122
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34256318"
---
# <a name="operator-windowsuixamlinteroptypename"></a>operator Windows::UI::Xaml::Interop::TypeName
Konwersja z umożliwia `Platform::Type` do [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
Operator TypeName(Platform::Type^ type)  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) , gdy `Platform::Type^`.  
  
### <a name="remarks"></a>Uwagi  
 `TypeName` jest niezależny od języka struktura środowiska wykonawczego systemu Windows reprezentująca informacji o typie. [Platform::type](../cppcx/platform-type-class.md) są specyficzne dla języka C++ i nie mogą być przekazywane przez interfejs binarne aplikacji (ABI). W tym miejscu stanowi jedno użycie `TypeName`w [Nawigacja](http://msdn.microsoft.com/library/windows/apps/hh702394.aspx) funkcji:  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
### <a name="example"></a>Przykład  
 W kolejnym przykładzie pokazano sposób konwertowania między `TypeName` i `Type`.  
  
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
 [Operator Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)   
 [Platform::Type, klasa](../cppcx/platform-type-class.md)