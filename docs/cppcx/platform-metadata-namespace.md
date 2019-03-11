---
title: Platform::METADATA Namespace
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata
helpviewer_keywords:
- Platform::Metadata Namespace
ms.assetid: e3e114d8-a4b0-47f0-865a-9ce9d7212e86
ms.openlocfilehash: 9626b3a9d28d28fd52a0d2295af8fda8855cd90c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739456"
---
# <a name="platformmetadata-namespace"></a>Platform::METADATA Namespace

Ta przestrzeń nazw zawiera atrybuty, które modyfikowania deklaracji typów.

## <a name="syntax"></a>Składnia

```cpp
namespace Platform {
   namespace Metadata {
}}
```

### <a name="members"></a>Elementy członkowskie

Chociaż ta przestrzeń nazw jest przeznaczony do użytku wewnętrznego, przeglądarki można wyświetlić następujące elementy członkowskie tej przestrzeni nazw.

|Nazwa|Uwagi|
|----------|------------|
|Atrybut|Klasę bazową dla atrybutów.|
|[Platform::Metadata::DefaultMemberAttribute, atrybut](../cppcx/platform-metadata-defaultmemberattribute-attribute.md)|Wskazuje preferowana funkcja do wywołania między kilka możliwych przeciążonej funkcji.|
|[Platform::METADATA:: flagsattribute, atrybut](../cppcx/platform-metadata-flagsattribute-attribute.md)flagi|Deklaruje wyliczenie, jako wyliczenie pól bitowych.<br /><br /> Poniższy przykład pokazuje, jak zastosować `Flags` atrybutu wyliczenia.<br /><br /> `[Flags] enum class MyEnumeration { enumA = 1, enumB = 2, enumC = 3}`|
|[Platform::Metadata::RuntimeClassNameAttribute](../cppcx/platform-metadata-runtimeclassname.md)|Zapewnia, że prywatnej klasy ref ma nazwę klasy środowiska uruchomieniowego prawidłowe.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Platform`

### <a name="requirements"></a>Wymagania

**Metadane:** platform.winmd

**Namespace:** Platform::METADATA

## <a name="see-also"></a>Zobacz także

[Namespace platformy](platform-namespace-c-cx.md)
