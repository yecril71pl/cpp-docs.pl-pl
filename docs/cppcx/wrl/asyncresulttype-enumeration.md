---
title: AsyncResultType — Wyliczenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: 309ed876c71f453336ecc2ed10eedc07f2a80be8
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787203"
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

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)