---
title: Platform::METADATA::RuntimeClassName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata::RuntimeClassName
helpviewer_keywords:
- RuntimeClassName
- Platform::Metadata::RuntimeClassName
ms.assetid: fdef8f85-ab94-4edd-ba50-ee0da9358ff6
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 297a5089af7db43d837934e864e0925cd7b34a3d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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