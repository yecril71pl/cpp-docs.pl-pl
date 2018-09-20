---
title: operator&lt; — Operator (Microsoft::WRL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator<
dev_langs:
- C++
ms.assetid: bfae0e1c-1648-482b-99c2-3217d62aba46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 077f21c92ea1d731b1427635ce5b60c45af0f5f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443361"
---
# <a name="operatorlt-operator-microsoftwrl"></a>operator&lt; — Operator (Microsoft::WRL)

Określa, czy adres jeden obiekt jest mniejszy niż inny.

## <a name="syntax"></a>Składnia

```cpp
template<class T, class U>
bool operator<(const ComPtr<T>& a, const ComPtr<U>& b) throw();
template<class T, class U>
bool operator<(const Details::ComPtrRef<ComPtr<T>>& a, const Details::ComPtrRef<ComPtr<U>>& b) throw();
```

### <a name="parameters"></a>Parametry

*a*<br/>
Obiekt, który po lewej stronie.

*b*<br/>
Obiekt, do prawej.

## <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli adres *a* jest mniejszy niż adres *b*; w przeciwnym razie **false**.

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)