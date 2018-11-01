---
title: Platform::Metadata::RuntimeClassName
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata::RuntimeClassName
helpviewer_keywords:
- RuntimeClassName
- Platform::Metadata::RuntimeClassName
ms.assetid: fdef8f85-ab94-4edd-ba50-ee0da9358ff6
ms.openlocfilehash: 09641f55e27ab00fc941d85d4d09d6a7784e2d8a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668276"
---
# <a name="platformmetadataruntimeclassname"></a>Platform::Metadata::RuntimeClassName

Po zastosowaniu do definicji klasy, zapewnia, że klasa prywatna zwraca prawidłową nazwę funkcji getruntimeclassname —...

## <a name="syntax"></a>Składnia

```cpp
[Platform::Metadata::RuntimeClassName] name
```

#### <a name="parameters"></a>Parametry

*Nazwa*<br/>
Nazwa istniejącego typu publiczne, która jest widoczna w środowisku uruchomieniowym Windows.

### <a name="remarks"></a>Uwagi

Użyj tego atrybutu na klasy ref prywatny, aby określić nazwę typu niestandardowego środowiska uruchomieniowego i/lub gdy istniejącej nazwy nie spełnia wymagań. Określ jako nazwę interfejsu publicznego, który implementuje klasa.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać atrybutu. W tym przykładzie nazwa typu środowiska uruchomieniowego HellowWorldImpl jest Test::Native::MyComponent::IHelloWorld

```cpp
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