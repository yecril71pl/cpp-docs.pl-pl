---
title: '_com_ptr_t:: oddziel | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7f2f44df96ca339e5d8e4b251b5f2d259cb606b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092144"
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