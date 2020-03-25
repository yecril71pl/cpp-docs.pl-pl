---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 870e3580ed23ce994d832f7c59b951680d725e41
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180501"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**Specyficzne dla firmy Microsoft**

Hermetyzuje pierwotny wskaźnik interfejsu tego typu inteligentnego wskaźnika.

## <a name="syntax"></a>Składnia

```
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>Parametry

*pInterface*<br/>
Pierwotny wskaźnik interfejsu.

*fAddRef*<br/>
Jeśli ma wartość TRUE, `AddRef` jest wywoływana. Jeśli ma wartość FALSE, obiekt `_com_ptr_t` przejmuje własność wskaźnika interfejsu RAW bez wywoływania `AddRef`.

## <a name="remarks"></a>Uwagi

- Nie wywołano metody **Attach (** *pInterface* **)** `AddRef`. Własność interfejsu jest przenoszona do tego obiektu `_com_ptr_t`. `Release` jest wywoływana, aby zmniejszyć liczbę odwołań dla poprzednio hermetyzowanego wskaźnika.

- **Attach (**  *pInterface* **,**  *fAddRef*  **)** Jeśli *fAddRef* ma wartość TRUE, `AddRef` jest wywoływana, aby zwiększyć liczbę odwołań dla wskaźnika hermetyzowanego interfejsu. Jeśli *fAddRef* ma wartość false, ten obiekt `_com_ptr_t` przejmuje własność wskaźnika interfejsu RAW bez wywoływania `AddRef`. `Release` jest wywoływana, aby zmniejszyć liczbę odwołań dla poprzednio hermetyzowanego wskaźnika.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)
