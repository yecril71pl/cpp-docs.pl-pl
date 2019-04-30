---
title: underlying_type, klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::underlying_type
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
ms.openlocfilehash: 23e5e9bc5406265f49fca2ed220c597cb32e2a9a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399366"
---
# <a name="underlyingtype-class"></a>underlying_type, klasa

Tworzy podstawowy typ całkowitą typ wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do modyfikacji.

## <a name="remarks"></a>Uwagi

`type` Typedef składowej klasy szablonu, nazwy podstawowy typ całkowitoliczbowy *T*, gdy *T* jest typem wyliczenia, w przeciwnym razie nie ma żadnych elementu członkowskiego typedef `type`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
