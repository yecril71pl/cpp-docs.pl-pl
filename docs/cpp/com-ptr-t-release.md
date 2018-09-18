---
title: _com_ptr_t::wydanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
dev_langs:
- C++
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 444f56c1a999f09a79d725173c9f0f19399ab363
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118365"
---
# <a name="comptrtrelease"></a>_com_ptr_t::Release

**Microsoft Specific**

Wywołania **wersji** funkcji składowej typu `IUnknown` interfejsu zhermetyzowanego wskaźnika.

## <a name="syntax"></a>Składnia

```
void Release( );
```

## <a name="remarks"></a>Uwagi

Wywołania `IUnknown::Release` wskaźnika zhermetyzowany interfejs wywoływanie `E_POINTER` błąd, jeśli ten wskaźnik interfejsu ma wartość NULL.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)