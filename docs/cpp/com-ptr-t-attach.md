---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 057d784bb495aefaeec1b86697a7421f6464cbd7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745066"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**Specyficzne dla firmy Microsoft**

Hermetyzuje wskaźnik interfejsu nieprzetworzonego typu tego inteligentnego wskaźnika.

## <a name="syntax"></a>Składnia

```cpp
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>Parametry

*pInterface (właso)*<br/>
Nieprzetworzony wskaźnik interfejsu.

*fOddRef*<br/>
Jeśli jest true, `AddRef` a następnie jest wywoływana. Jeśli jest false, `_com_ptr_t` obiekt przejmuje na własność nieprzetworzony wskaźnik interfejsu bez wywoływania `AddRef`.

## <a name="remarks"></a>Uwagi

- **Attach(**  *pInterface*  **)** `AddRef` nie jest wywoływana. Własność interfejsu jest przekazywana `_com_ptr_t` do tego obiektu. `Release`jest wywoływana w celu zdekrostu liczby odwołań dla wcześniej zhermetyzowanego wskaźnika.

- **Dołącz(**  *pInterface* **,**  *fAddRef*  **)** Jeśli *fAddRef* ma `AddRef` wartość PRAWDA, jest wywoływana w celu zwiększenie liczby odwołań dla zhermetyzowanego wskaźnika interfejsu. Jeśli *fAddRef* jest `_com_ptr_t` FALSE, ten obiekt przejmuje na `AddRef`własność wskaźnik interfejsu nieprzetworzonego bez wywoływania . `Release`jest wywoływana w celu zdekrostu liczby odwołań dla wcześniej zhermetyzowanego wskaźnika.

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_ptr_t — Klasa](../cpp/com-ptr-t-class.md)
