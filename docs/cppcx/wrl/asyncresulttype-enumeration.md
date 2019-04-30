---
title: AsyncResultType — Wyliczenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: d3f99fa85a777ae8361ed6f7cb82fe97ddd8d667
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398800"
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

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)