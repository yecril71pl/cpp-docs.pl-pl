---
title: _bstr_t — Klasa
ms.date: 11/04/2016
f1_keywords:
- _bstr_t
helpviewer_keywords:
- BSTR object
- _bstr_t class
- BSTR object [C++], COM encapsulation
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
ms.openlocfilehash: 3ef89c6f6742d528c427c49fd2a62d8820625e79
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190381"
---
# <a name="_bstr_t-class"></a>_bstr_t — Klasa

**Specyficzne dla firmy Microsoft**

Obiekt `_bstr_t` hermetyzuje [Typ danych BSTR](/previous-versions/windows/desktop/automat/bstr). Klasa zarządza alokacją zasobów i dealokacją przez wywołania funkcji w celu `SysAllocString` i `SysFreeString` i innych `BSTR` interfejsów API, jeśli jest to konieczne. Klasa **_bstr_t** używa zliczania odwołań, aby uniknąć nadmiernego obciążenia.

### <a name="construction"></a>Zrekonstruowan

|||
|-|-|
|[_bstr_t](../cpp/bstr-t-bstr-t.md)|Konstruuje obiekt `_bstr_t`.|

### <a name="operations"></a>Operacje

|||
|-|-|
|[Assign](../cpp/bstr-t-assign.md)|Kopiuje `BSTR` do `BSTR` opakowane `_bstr_t`.|
|[Attach](../cpp/bstr-t-attach.md)|Łączy otokę `_bstr_t` z `BSTR`.|
|[kopiowane](../cpp/bstr-t-copy.md)|Tworzy kopię hermetyzowanej `BSTR`.|
|[Detach](../cpp/bstr-t-detach.md)|Zwraca `BSTR` opakowany `_bstr_t` i odłącza `BSTR` od `_bstr_t`.|
|[GetAddress](../cpp/bstr-t-getaddress.md)|Wskazuje `BSTR` opakowany przez `_bstr_t`.|
|[GetBSTR](../cpp/bstr-t-getbstr.md)|Wskazuje początek `BSTR` opakowany przez `_bstr_t`.|
|[Długość](../cpp/bstr-t-length.md)|Zwraca liczbę znaków w `_bstr_t`.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](../cpp/bstr-t-operator-equal.md)|Przypisuje nową wartość do istniejącego obiektu `_bstr_t`.|
|[operator + =](../cpp/bstr-t-operator-add-equal-plus.md)|Dołącza znaki na końcu obiektu `_bstr_t`.|
|[operator +](../cpp/bstr-t-operator-add-equal-plus.md)|Łączy dwa ciągi.|
|[operator !](../cpp/bstr-t-operator-logical-not.md)|Sprawdza, czy hermetyzowany `BSTR` jest ciągiem o wartości NULL.|
|[operator = =,! =, \<, >, \<=, > =](../cpp/bstr-t-relational-operators.md)|Porównuje dwa obiekty `_bstr_t`.|
|[operator wchar_t * &#124; char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|Wyodrębnij wskaźniki do hermetyzowanego obiektu `BSTR` Unicode lub wielobajtowego.|

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<comutil. h >

**Lib:** comsuppw. lib lub comsuppwd. lib (patrz [/Zc: Wchar_t (Wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) , aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Kompilator klas obsługi COM](../cpp/compiler-com-support-classes.md)
