---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 4b4b7a21d12cc645c486dd93d555510c1e716563
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566546"
---
# <a name="comptrtattach"></a>_com_ptr_t::Attach

**Microsoft Specific**

Hermetyzuje surowego wskaźnika interfejsu tego inteligentnego wskaźnika typu.

## <a name="syntax"></a>Składnia

```
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>Parametry

*pInterface*<br/>
Surowego wskaźnika interfejsu.

*fAddRef*<br/>
Jeśli ma wartość PRAWDA, następnie `AddRef` jest wywoływana. Jeśli wartość FAŁSZ, `_com_ptr_t` obiektu przejmuje na własność surowego wskaźnika interfejsu bez wywoływania `AddRef`.

## <a name="remarks"></a>Uwagi

- **Dołącz (***pInterface***)** `AddRef` nie zostanie wywołana. Własność interfejsu jest przekazywany do tego `_com_ptr_t` obiektu. `Release` jest wywoływana, aby zmniejszyć licznikiem odwołań do wcześniej zhermetyzowanego wskaźnika.

- **Dołącz (***pInterface* **,***fAddRef***)** Jeśli *fAddRef* ma wartość PRAWDA, `AddRef`jest wywoływana, aby zwiększyć licznik odwołań dla interfejsu zhermetyzowanego wskaźnika. Jeśli *fAddRef* ma wartość FAŁSZ, to `_com_ptr_t` obiektu przejmuje na własność surowego wskaźnika interfejsu bez wywoływania `AddRef`. `Release` jest wywoływana, aby zmniejszyć licznikiem odwołań do wcześniej zhermetyzowanego wskaźnika.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)