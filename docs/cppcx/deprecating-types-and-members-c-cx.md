---
title: "Wycofano typy i składniki (C + +/ CX) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.prod: windows-client-threshold
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 0fbed1c29feccc6a999545daab6be8bd9ccfc7f9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="deprecating-types-and-members-ccx"></a>Wycofano typy i składniki (C + +/ CX)
W języku C + +/ CX, amortyzacja typów środowiska wykonawczego systemu Windows i elementów członkowskich, producenci i konsumenci przy użyciu [przestarzały](http://msdn.microsoft.com/en-us/8b02ad36-3b5f-4361-888b-e6a99040e57c) atrybut jest obsługiwany. Możesz korzystać z interfejsu API, do których zastosowano ten atrybut, otrzymasz komunikat ostrzegawczy kompilacji, który wskazuje, że interfejs API jest przestarzały i zaleca także alternatywne API do użycia. Własne typy publiczne i metody można zastosować ten atrybut i podaj własnego niestandardowego komunikatu.  
  
> [!CAUTION]
>  [Przestarzały](http://msdn.microsoft.com/en-us/8b02ad36-3b5f-4361-888b-e6a99040e57c) atrybutu ma być używany tylko z typami środowiska wykonawczego systemu Windows. Standardowa klas C++ i elementów członkowskich, należy użyć [__declspec(deprecated)](http://msdn.microsoft.com/library/044swk7y.aspx).  
  
### <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można zastąpić własnych publicznych interfejsach API — na przykład w składnika środowiska wykonawczego systemu Windows. Drugi parametr typu [systemu Windows: Foundation:: Metadata::DeprecationType](http://msdn.microsoft.com/en-us/ee01e63d-37d0-4273-accc-fca174f88bfa) Określa, czy interfejs API jest przestarzały lub usunięty. Obecnie tylko DeprecationType::Deprecated wartość jest obsługiwana. Trzeci parametr w atrybucie Określa [Windows::Foundation::Metadata::Platform](http://msdn.microsoft.com/en-us/1eae292d-1ab7-4d97-a58c-b0beffd51ef5) którego dotyczy ten atrybut.  
  
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
 W poniższej tabeli wymieniono konstrukcje, których można zastosować atrybutu uznane za przestarzałe:  
  
||  
|-|  
|Kontrolki XAML|  
|delegate|  
|zdarzenie|  
|pole Enum|  
|enum|  
|struktura |  
|— metoda|  
|class|  
|interface|  
|property|  
|Pole struktury|  
|Konstruktor sparametryzowane|  
  
## <a name="see-also"></a>Zobacz też  
 [System typów](../cppcx/type-system-c-cx.md)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)