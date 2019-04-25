---
title: _com_ptr_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Detach
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
ms.openlocfilehash: affaefd8af4802836733587af62977171ba01410
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154971"
---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach

**Microsoft Specific**

Wyodrębnia i zwraca wskaźnik zhermetyzowany interfejs.

## <a name="syntax"></a>Składnia

```
Interface* Detach( ) throw( );
```

## <a name="remarks"></a>Uwagi

Wyodrębnia i zwraca wskaźnik zhermetyzowany interfejs, a następnie czyści magazyn zhermetyzowanego wskaźnika o wartości NULL. Spowoduje to usunięcie wskaźnika interfejsu z hermetyzacji. Aby wywołać to `Release` na wskaźnik interfejsu zwrócone.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)