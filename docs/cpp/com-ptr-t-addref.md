---
title: _com_ptr_t::AddRef
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::AddRef
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
ms.openlocfilehash: 51182b461aeac83c12bb18a573a49b2d4347a190
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189936"
---
# <a name="_com_ptr_taddref"></a>_com_ptr_t::AddRef

**Specyficzne dla firmy Microsoft**

Wywołuje `AddRef` funkcji składowej `IUnknown` na hermetyzowanym wskaźniku interfejsu.

## <a name="syntax"></a>Składnia

```
void AddRef( );
```

## <a name="remarks"></a>Uwagi

Wywołuje `IUnknown::AddRef` na hermetyzowanym wskaźniku interfejsu, wywołując błąd `E_POINTER`, jeśli wskaźnik ma wartość NULL.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)
