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
ms.openlocfilehash: f521681da10eeda3b8024b0865d5164021296353
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838714"
---
# <a name="_bstr_t-class"></a>_bstr_t — Klasa

**Specyficzne dla firmy Microsoft**

`_bstr_t`Obiekt hermetyzuje [Typ danych BSTR](/previous-versions/windows/desktop/automat/bstr). Klasa zarządza alokacją zasobów i dealokacją przez wywołania funkcji do `SysAllocString` i `SysFreeString` i inne `BSTR` interfejsy API, jeśli jest to konieczne. Klasa **_bstr_t** używa zliczania odwołań, aby uniknąć nadmiernego obciążenia.

### <a name="construction"></a>Budownictwo

| Konstruktor | Opis |
|--|--|
| [_bstr_t](../cpp/bstr-t-bstr-t.md) | Konstruuje `_bstr_t` obiekt. |

### <a name="operations"></a>Operacje

| Funkcja | Opis |
|--|--|
| [Ponownie](../cpp/bstr-t-assign.md) | Kopiuje `BSTR` do `BSTR` opakowany przez `_bstr_t` . |
| [Dołącz](../cpp/bstr-t-attach.md) | Łączy `_bstr_t` otokę z `BSTR` . |
| [kopiowane](../cpp/bstr-t-copy.md) | Tworzy kopię hermetyzowania `BSTR` . |
| [Odłącz](../cpp/bstr-t-detach.md) | Zwraca `BSTR` opakowany przez a `_bstr_t` i odłącza `BSTR` od `_bstr_t` . |
| [GetAddress](../cpp/bstr-t-getaddress.md) | Wskazuje na `BSTR` opakowane przez `_bstr_t` . |
| [GetBSTR](../cpp/bstr-t-getbstr.md) | Wskazuje początek `BSTR` opakowany przez `_bstr_t` . |
| [Długość](../cpp/bstr-t-length.md) | Zwraca liczbę znaków w `_bstr_t` . |

### <a name="operators"></a>Operatory

| Operator | Opis |
|--|--|
| [operator =](../cpp/bstr-t-operator-equal.md) | Przypisuje nową wartość do istniejącego `_bstr_t` obiektu. |
| [operator + =](../cpp/bstr-t-operator-add-equal-plus.md) | Dołącza znaki do końca `_bstr_t` obiektu. |
| [operator +](../cpp/bstr-t-operator-add-equal-plus.md) | Łączy dwa ciągi. |
| [zakład!](../cpp/bstr-t-operator-logical-not.md) | Sprawdza, czy hermetyzowany `BSTR` jest pustym ciągiem. |
| [operator = =,! =, \<, > , \<=, >=](../cpp/bstr-t-relational-operators.md) | Porównuje dwa `_bstr_t` obiekty. |
| [operator wchar_t * &#124; char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md) | Wyodrębnij wskaźniki do zhermetyzowanego obiektu Unicode lub wielobajtowego `BSTR` . |

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<comutil.h>

**Lib:** comsuppw. lib lub comsuppwd. lib (patrz [/Zc: Wchar_t (Wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) , aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Klasy obsługi kompilatora COM](../cpp/compiler-com-support-classes.md)
