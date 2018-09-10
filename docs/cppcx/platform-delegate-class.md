---
title: Platform::Delegate, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Delegate
dev_langs:
- C++
helpviewer_keywords:
- Platform::Delegate Class
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78ac7cce43dbe08097c1e7b78423fadafc7f5309
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101914"
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

Użyj [delegować](../windows/delegate-cpp-component-extensions.md) — słowo kluczowe do tworzenia obiektów delegowanych; nie należy używać Platform::Delegate jawnie. Aby uzyskać więcej informacji, zobacz [delegatów](../cppcx/delegates-c-cx.md). Na przykład sposobu tworzenia i wykorzystywania delegata zobacz [Tworzenie składników środowiska wykonawczego Windows w języku C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** systemu Windows 8

**Minimalna obsługiwana serwera:** systemu Windows Server 2012

**Namespace:** platformy

**Metadane:** platform.winmd

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)