---
title: _variant_t — Ekstraktory
ms.date: 11/04/2016
f1_keywords:
- _variant_t.operatordouble
- operatorlong
- _variant_t::operator_bstr_t
- operatordouble
- _variant_t.operatorCY
- operatorCY
- _variant_t::operatorCY
- _variant_t::operatordouble
- operatorfloat
- operatorBYTE
- _variant_t.operatorDECIMAL
- _variant_t::operatorlong
- operatorIDispatch
- _variant_t.operatorBYTE
- operatorDECIMAL
- _variant_t.operator_bstr_t
- _variant_t::operatorDECIMAL
- _variant_t.operatorIUnknown
- _variant_t.operatorlong
- _variant_t::operatorIDispatch
- _variant_t::operatorIUnknown
- operatorIUnknown
- _variant_t.operatorbool
- _variant_t::operatorBYTE
- _variant_t.operatorfloat
- operator_bstr_t
- _variant_t::operatorbool
- operatorshort
- _variant_t::operatorshort
- _variant_t::operatorfloat
- _variant_t.operatorIDispatch
- _variant_t.operatorshort
helpviewer_keywords:
- extractors, _variant_t class
- operator CY
- operator IDispatch
- operator SHORT
- operator double
- operator long
- operator _bstr_t
- operator DECIMAL
- operator float
- operator bool
- operator BYTE
- operator IUnknown
ms.assetid: 33c1782f-045a-4673-9619-1d750efc83a9
ms.openlocfilehash: 685df7285e58e0cf2ceeded5ac27641364897298
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187703"
---
# <a name="_variant_t-extractors"></a>_variant_t — Ekstraktory

**Specyficzne dla firmy Microsoft**

Wyodrębnij dane z hermetyzowanego obiektu `VARIANT`.

## <a name="syntax"></a>Składnia

```
operator short( ) const;
operator long( ) const;
operator float( ) const;
operator double( ) const;
operator CY( ) const;
operator _bstr_t( ) const;
operator IDispatch*( ) const;
operator bool( ) const;
operator IUnknown*( ) const;
operator DECIMAL( ) const;
operator BYTE( ) const;
operator VARIANT() const throw();
operator char() const;
operator unsigned short() const;
operator unsigned long() const;
operator int() const;
operator unsigned int() const;
operator __int64() const;
operator unsigned __int64() const;
```

## <a name="remarks"></a>Uwagi

Wyodrębnia pierwotne dane z hermetyzowanej `VARIANT`. Jeśli `VARIANT` nie jest jeszcze właściwym typem, `VariantChangeType` jest używany do próby konwersji, a w przypadku niepowodzenia zostanie wygenerowany błąd:

- **operator short ()** Wyodrębnia **krótką** wartość całkowitą.

- **Długość operatora ()** Wyodrębnia wartość **Long** Integer.

- **zmiennoprzecinkowy operatora ()** Wyodrębnia wartość liczbową **zmiennoprzecinkową** .

- **operator Double ()** Wyodrębnia wartość o **podwójnej** liczbie całkowitej.

- **operator cy ()** Wyodrębnia obiekt `CY`.

- wartość **logiczna operatora ()** Wyodrębnia wartość **logiczną** .

- **liczba dziesiętna operatora ()** Wyodrębnia wartość `DECIMAL`.

- **bajt operatora ()** Wyodrębnia wartość `BYTE`.

- **_bstr_t operatora ()** Wyodrębnia ciąg, który jest hermetyzowany w obiekcie `_bstr_t`.

- **\*operatora IDispatch ()** Wyodrębnia wskaźnik dispinterface z hermetyzowanej `VARIANT`. `AddRef` jest wywoływana na wskaźniku będącym wynikiem, dlatego można wywołać `Release`, aby go zwolnić.

- **\*operatora IUnknown ()** Wyodrębnia wskaźnik interfejsu COM z hermetyzowanej `VARIANT`. `AddRef` jest wywoływana na wskaźniku będącym wynikiem, dlatego można wywołać `Release`, aby go zwolnić.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_variant_t, klasa](../cpp/variant-t-class.md)
