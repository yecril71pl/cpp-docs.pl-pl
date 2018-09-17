---
title: underlying_type, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::underlying_type
dev_langs:
- C++
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e9c1ab3ceb4965450f89de3b483915d693b5100
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711649"
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
