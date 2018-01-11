---
title: Platform::METADATA::RuntimeClassName | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/Platform::Metadata::RuntimeClassName
helpviewer_keywords:
- RuntimeClassName
- Platform::Metadata::RuntimeClassName
ms.assetid: fdef8f85-ab94-4edd-ba50-ee0da9358ff6
caps.latest.revision: "2"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8c32ac79cbea1425af42576073b2f59ef6a562a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="platformmetadataruntimeclassname"></a>Platform::Metadata::RuntimeClassName
Gdy jest stosowany do definicji klasy, zapewnia Klasa prywatna zwracanych prawidłową nazwą funkcji GetRuntimeClassName...  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
[Platform::Metadata::RuntimeClassName] name  
```  
  
#### <a name="parameters"></a>Parametry  
 nazwa  
  
 Nazwa istniejącej typu publicznego, widocznego w środowisku wykonawczym systemu Windows.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego atrybutu na klasy ref prywatne, aby określić nazwę typu niestandardowego środowisko uruchomieniowe i/lub gdy istniejącej nazwy nie spełnia wymagań. Określ jako nazwa interfejsu publicznego, który implementuje klasy.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie atrybutu. W tym przykładzie nazwa typu środowiska uruchomieniowego HellowWorldImpl jest Test::Native::MyComponent::IHelloWorld  
  
```  
  
namespace Test  
{  
    namespace Native  
    {  
        namespace MyComponent  
        {  
            public interface class IHelloWorld  
            {  
                Platform::String^ SayHello();  
            };  
  
            private ref class HelloWorldImpl sealed :[Platform::Metadata::RuntimeClassName] IHelloWorld  
            {  
            public:  
                HelloWorldImpl();  
                virtual Platform::String^ SayHello();  
            };  
  
            Platform::String^ HelloWorldImpl::SayHello()  
            {  
                return L"Hello World!";  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Platform::Metadata, przestrzeń nazw](../cppcx/platform-metadata-namespace.md)