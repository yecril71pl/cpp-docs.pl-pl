---
title: AsyncResultType — Wyliczenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: df91b80fe21ecddabc7062b040387b8c2b2c1bb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551375"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType — Wyliczenie

Określa typ wyniku zwracanego przez `GetResults()` metody.

## <a name="syntax"></a>Składnia

```cpp
enum AsyncResultType;
```

## <a name="members"></a>Elementy członkowskie

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`MultipleResults`|Zbiór wielu wyników, które są prezentowane stopniowo między `Start` stanu i przed `Close()` jest wywoływana.|
|`SingleResult`|Pojedynczy wynik, który jest przedstawiony po `Complete` wystąpi zdarzenie.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)