---
title: _com_ptr_t::AddRef
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::AddRef
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
ms.openlocfilehash: 7408b5c174f76673b56caffd56aaa87895bd08d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154945"
---
# <a name="comptrtaddref"></a>_com_ptr_t::AddRef

**Microsoft Specific**

Wywołania `AddRef` funkcji składowej typu `IUnknown` interfejsu zhermetyzowanego wskaźnika.

## <a name="syntax"></a>Składnia

```
void AddRef( );
```

## <a name="remarks"></a>Uwagi

Wywołania `IUnknown::AddRef` wskaźnika zhermetyzowany interfejs wywoływanie `E_POINTER` błędu, jeśli wskaźnik jest pusty.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)