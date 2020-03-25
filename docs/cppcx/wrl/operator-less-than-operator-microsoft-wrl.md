---
title: 'operator&lt; operatora (Microsoft:: WRL)'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator<
ms.assetid: bfae0e1c-1648-482b-99c2-3217d62aba46
ms.openlocfilehash: 04f5598667f7e0e036f0a55cd3f9cc52b5356299
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213645"
---
# <a name="operatorlt-operator-microsoftwrl"></a>operator&lt; operatora (Microsoft:: WRL)

Określa, czy adres jednego obiektu jest mniejszy niż inny.

## <a name="syntax"></a>Składnia

```cpp
template<class T, class U>
bool operator<(const ComPtr<T>& a, const ComPtr<U>& b) throw();
template<class T, class U>
bool operator<(const Details::ComPtrRef<ComPtr<T>>& a, const Details::ComPtrRef<ComPtr<U>>& b) throw();
```

### <a name="parameters"></a>Parametry

*z*<br/>
Lewy obiekt.

*b*<br/>
Prawidłowy obiekt.

## <a name="return-value"></a>Wartość zwracana

**prawda** *, jeśli adres jest mniejszy* niż adres *b*; w przeciwnym razie **false**.

## <a name="requirements"></a>Wymagania

**Nagłówek:** Client. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)
