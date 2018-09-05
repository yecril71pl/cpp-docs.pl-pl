---
title: Wycofane typy i składowe (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b2f8ab1c52297a95c89f8ee00053d24baebe39d
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764413"
---
# <a name="deprecating-types-and-members-ccx"></a>Wycofane typy i składowe (C + +/ CX)
W języku C + +/ CX, amortyzacja typów środowiska wykonawczego Windows i elementów członkowskich dla producentów i konsumentów, za pomocą [uznane za przestarzałe](/uwp/api/windows.foundation.metadata.deprecatedattribute) atrybut jest obsługiwany. Jeśli wykorzystasz interfejsu API, do którego zastosowano ten atrybut, otrzymasz komunikat ostrzegawczy kompilacji, która wskazuje, że interfejs API jest przestarzały i zaleca również alternatywny interfejsu API do użycia. We własnych typów publicznych i metody można zastosować ten atrybut i Podaj własny niestandardowy komunikat.  
  
> [!CAUTION]
>  [Uznane za przestarzałe](/uwp/api/windows.foundation.metadata.deprecatedattribute) atrybut jest tylko do użytku z typami środowiska wykonawczego Windows. W przypadku standardowych klas C++ i elementów członkowskich, użyj [__declspec(deprecated)](../cpp/deprecated-cpp.md).  
  
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
  
||  
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
  
## <a name="see-also"></a>Zobacz też  
 [System typów](../cppcx/type-system-c-cx.md)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)