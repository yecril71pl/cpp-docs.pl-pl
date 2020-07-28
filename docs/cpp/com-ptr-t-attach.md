---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: cb5950e311711dd489b3cab223714b1840773f60
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220590"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**Specyficzne dla firmy Microsoft**

Hermetyzuje pierwotny wskaźnik interfejsu tego typu inteligentnego wskaźnika.

## <a name="syntax"></a>Składnia

```cpp
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>Parametry

*pInterface*<br/>
Pierwotny wskaźnik interfejsu.

*fAddRef*<br/>
Jeśli jest **`true`** , to `AddRef` jest wywoływana. Jeśli tak **`false`** , `_com_ptr_t` obiekt przejmuje własność wskaźnika interfejsu RAW bez wywoływania `AddRef` .

## <a name="remarks"></a>Uwagi

- **Dołącz (**  *pInterface*  **)** `AddRef` nie jest wywoływana. Własność interfejsu jest przenoszona do tego `_com_ptr_t` obiektu. `Release`jest wywoływana, aby zmniejszyć liczbę odwołań dla poprzednio hermetyzowanego wskaźnika.

- **Attach (**  *pInterface* **,**  *fAddRef*  **)** Jeśli *fAddRef* jest **`true`** , `AddRef` jest wywoływana, aby zwiększyć liczbę odwołań dla wskaźnika hermetyzowanego interfejsu. Jeśli *fAddRef* jest **`false`** , ten `_com_ptr_t` obiekt przejmuje własność wskaźnika interfejsu RAW bez wywoływania `AddRef` . `Release`jest wywoływana, aby zmniejszyć liczbę odwołań dla poprzednio hermetyzowanego wskaźnika.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Klasa _com_ptr_t](../cpp/com-ptr-t-class.md)
