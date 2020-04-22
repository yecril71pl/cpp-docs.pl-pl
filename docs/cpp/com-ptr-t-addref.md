---
title: _com_ptr_t::AddRef
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::AddRef
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
ms.openlocfilehash: 4dcf643357c9b368d4b2ea3bc51e6567acf45a44
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745093"
---
# <a name="_com_ptr_taddref"></a>_com_ptr_t::AddRef

**Specyficzne dla firmy Microsoft**

Wywołuje `AddRef` funkcję elementu `IUnknown` członkowskiego na wskaźnik interfejsu zhermetyzowany.

## <a name="syntax"></a>Składnia

```cpp
void AddRef( );
```

## <a name="remarks"></a>Uwagi

Wywołuje `IUnknown::AddRef` zhermetyzowany wskaźnik interfejsu, `E_POINTER` podnosząc błąd, jeśli wskaźnik ma wartość NULL.

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_ptr_t — Klasa](../cpp/com-ptr-t-class.md)
