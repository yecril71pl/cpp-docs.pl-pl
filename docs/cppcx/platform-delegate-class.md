---
title: Platform::Delegate, klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Delegate
helpviewer_keywords:
- Platform::Delegate Class
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
ms.openlocfilehash: 4116de3240c3ef334db51095997f946731372708
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58769241"
---
# <a name="platformdelegate-class"></a>Platform::Delegate, klasa

Reprezentuje obiekt funkcyjny.

## <a name="syntax"></a>Składnia

```cpp
public delegate void delegate_name();
```

### <a name="members"></a>Elementy członkowskie

Klasa obiektu delegowanego ma metodę Equals, element GetHashCode(), i metody ToString() pochodną [Platform::Object, klasa](../cppcx/platform-object-class.md).

### <a name="remarks"></a>Uwagi

Użyj [delegować](../extensions/delegate-cpp-component-extensions.md) — słowo kluczowe do tworzenia obiektów delegowanych; nie należy używać Platform::Delegate jawnie. Aby uzyskać więcej informacji, zobacz [delegatów](../cppcx/delegates-c-cx.md). Na przykład sposobu tworzenia i wykorzystywania delegata zobacz [Tworzenie składników środowiska wykonawczego Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** Windows 8

**Minimalna obsługiwana serwera:** Windows Server 2012

**Namespace:** Platforma

**Metadane:** platform.winmd

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
