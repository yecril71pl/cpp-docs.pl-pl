---
title: _variant_t::_variant_t
ms.date: 11/04/2016
f1_keywords:
- _variant_t::_variant_t
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
ms.openlocfilehash: 50c10eb4ff617f4bcdc69d2e1781a9920b9eb0e5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233564"
---
# <a name="_variant_t_variant_t"></a>_variant_t::_variant_t

**Specyficzne dla firmy Microsoft**

Konstruuje `_variant_t` obiekt.

## <a name="syntax"></a>Składnia

```
_variant_t( ) throw( );

_variant_t(
   const VARIANT& varSrc
);

_variant_t(
   const VARIANT* pVarSrc
);

_variant_t(
   const _variant_t& var_t_Src
);

_variant_t(
   VARIANT& varSrc,
   bool fCopy
);

_variant_t(
   short sSrc,
   VARTYPE vtSrc = VT_I2
);

_variant_t(
   long lSrc,
   VARTYPE vtSrc = VT_I4
);

_variant_t(
   float fltSrc
) throw( );

_variant_t(
   double dblSrc,
   VARTYPE vtSrc = VT_R8
);

_variant_t(
   const CY& cySrc
) throw( );

_variant_t(
   const _bstr_t& bstrSrc
);

_variant_t(
   const wchar_t *wstrSrc
);

_variant_t(
   const char* strSrc
);

_variant_t(
   IDispatch* pDispSrc,
   bool fAddRef = true
) throw( );

_variant_t(
   bool bSrc
) throw( );

_variant_t(
   IUnknown* pIUknownSrc,
   bool fAddRef = true
) throw( );

_variant_t(
   const DECIMAL& decSrc
) throw( );

_variant_t(
   BYTE bSrc
) throw( );

variant_t(
   char cSrc
) throw();

_variant_t(
   unsigned short usSrc
) throw();

_variant_t(
   unsigned long ulSrc
) throw();

_variant_t(
   int iSrc
) throw();

_variant_t(
   unsigned int uiSrc
) throw();

_variant_t(
   __int64 i8Src
) throw();

_variant_t(
   unsigned __int64 ui8Src
) throw();
```

#### <a name="parameters"></a>Parametry

*varSrc*<br/>
`VARIANT`Obiekt, który ma zostać skopiowany do nowego `_variant_t` obiektu.

*pVarSrc*<br/>
Wskaźnik do `VARIANT` obiektu, który ma zostać skopiowany do nowego `_variant_t` obiektu.

*var_t_Src*<br/>
`_variant_t`Obiekt, który ma zostać skopiowany do nowego `_variant_t` obiektu.

*fCopy*<br/>
Jeśli **`false`** dostarczony `VARIANT` obiekt jest dołączony do nowego `_variant_t` obiektu bez tworzenia nowej kopii przez `VariantCopy` .

*ISrc, sSrc*<br/>
Wartość całkowita do skopiowania do nowego `_variant_t` obiektu.

*vtSrc*<br/>
`VARTYPE`Dla nowego `_variant_t` obiektu.

*fltSrc, dblSrc*<br/>
Wartość liczbowa do skopiowania do nowego `_variant_t` obiektu.

*cySrc*<br/>
`CY`Obiekt, który ma zostać skopiowany do nowego `_variant_t` obiektu.

*bstrSrc*<br/>
`_bstr_t`Obiekt, który ma zostać skopiowany do nowego `_variant_t` obiektu.

*strSrc, wstrSrc*<br/>
Ciąg, który ma zostać skopiowany do nowego `_variant_t` obiektu.

*bSrc*<br/>
**`bool`** Wartość, która ma zostać skopiowana do nowego `_variant_t` obiektu.

*pIUknownSrc*<br/>
Wskaźnik interfejsu COM do obiektu VT_UNKNOWN, który ma być hermetyzowany do nowego `_variant_t` obiektu.

*pDispSrc*<br/>
Wskaźnik interfejsu COM do obiektu VT_DISPATCH, który ma być hermetyzowany do nowego `_variant_t` obiektu.

*decSrc*<br/>
`DECIMAL`Wartość, która ma zostać skopiowana do nowego `_variant_t` obiektu.

*bSrc*<br/>
`BYTE`Wartość, która ma zostać skopiowana do nowego `_variant_t` obiektu.

*cSrc*<br/>
**`char`** Wartość, która ma zostać skopiowana do nowego `_variant_t` obiektu.

*usSrc*<br/>
**`unsigned short`** Wartość, która ma zostać skopiowana do nowego `_variant_t` obiektu.

*ulSrc*<br/>
**`unsigned long`** Wartość, która ma zostać skopiowana do nowego `_variant_t` obiektu.

*iSrc*<br/>
**`int`** Wartość, która ma zostać skopiowana do nowego `_variant_t` obiektu.

*uiSrc*<br/>
**`unsigned int`** Wartość, która ma zostać skopiowana do nowego `_variant_t` obiektu.

*i8Src*<br/>
**`__int64`** Wartość, która ma zostać skopiowana do nowego `_variant_t` obiektu.

*ui8Src*<br/>
Wartość **__int64 bez znaku** do skopiowania do nowego `_variant_t` obiektu.

## <a name="remarks"></a>Uwagi

- **_variant_t ()** Konstruuje pusty `_variant_t` obiekt, `VT_EMPTY` .

- **_variant_t (wariant&** *varSrc***)** Konstruuje `_variant_t` obiekt z kopii `VARIANT` obiektu.     Typ Variant jest zachowywany.

- **_variant_t (wariant** <strong>\*</strong> *pVarSrc***)** konstruuje `_variant_t` obiekt z kopii `VARIANT` obiektu.     Typ Variant jest zachowywany.

- **_variant_t (_variant_t&** *var_t_Src***)** Konstruuje `_variant_t` obiekt z innego `_variant_t` obiektu.     Typ Variant jest zachowywany.

- **_variant_t (wariant&** *varSrc* **, bool** `fCopy` **)** konstruuje `_variant_t` obiekt z istniejącego `VARIANT` obiektu.       Jeśli *fCopy* jest **`false`** , obiekt **Variant** jest dołączony do nowego obiektu bez tworzenia kopii.

- **_variant_t (Short***sSrc* **, VARTYPE** `vtSrc` **= VT_I2)** konstruuje `_variant_t` obiekt typu VT_I2 lub VT_BOOL z **`short`** wartości całkowitej.       Inne `VARTYPE` wyniki w E_INVALIDARG błędzie.

- **_variant_t (Long** `lSrc` **, VARTYPE** `vtSrc` **= VT_I4)** konstruuje `_variant_t` obiekt typu VT_I4, VT_BOOL lub VT_ERROR z **`long`** wartości całkowitej.       Inne `VARTYPE` wyniki w E_INVALIDARG błędzie.

- **_variant_t (float** `fltSrc` **)** konstruuje `_variant_t` obiekt typu VT_R4 z **`float`** wartości liczbowej.    

- **_variant_t (Double** `dblSrc` **, VARTYPE** `vtSrc` **= VT_R8)** konstruuje `_variant_t` obiekt typu VT_R8 lub VT_DATE z **`double`** wartości liczbowej.       Inne `VARTYPE` wyniki w E_INVALIDARG błędzie.

- **_variant_t (cy&** `cySrc` **)** konstruuje `_variant_t` obiekt typu VT_CY z `CY` obiektu.    

- **_variant_t (_bstr_t&** `bstrSrc` **)** konstruuje `_variant_t` obiekt typu VT_BSTR z `_bstr_t` obiektu.     Przydzielono nowy `BSTR` .

- **_variant_t (wchar_t** <strong>\*</strong> *wstrSrc*  **)** konstruuje `_variant_t` obiekt typu VT_BSTR z ciągu Unicode. Przydzielono nowy `BSTR` .

- **_variant_t (Char** <strong>\*</strong> `strSrc` **)** Konstruuje `_variant_t` obiekt typu VT_BSTR z ciągu.     Przydzielono nowy `BSTR` .

- **_variant_t (bool** `bSrc` **)** konstruuje `_variant_t` obiekt typu VT_BOOL z **`bool`** wartości.    

- **_variant_t (IUnknown** <strong>\*</strong> `pIUknownSrc` **, bool** `fAddRef` **= true)** Konstruuje `_variant_t` obiekt typu VT_UNKNOWN ze wskaźnika interfejsu com.       Jeśli `fAddRef` jest **`true`** , `AddRef` to jest wywoływana na podanym wskaźniku interfejsu w celu dopasowania do wywołania `Release` , które pojawi się, gdy `_variant_t` obiekt zostanie zniszczony. Jest to możliwe do wywołania `Release` na podanym wskaźniku interfejsu. Jeśli `fAddRef` jest **`false`** , ten Konstruktor przejmuje własność dostarczonego wskaźnika interfejsu; nie wywołuj do `Release` podanego wskaźnika interfejsu.

- **_variant_t (IDispatch** <strong>\*</strong> `pDispSrc` **, bool** `fAddRef` **= true)** Konstruuje `_variant_t` obiekt typu VT_DISPATCH ze wskaźnika interfejsu com.       Jeśli `fAddRef` jest **`true`** , `AddRef` to jest wywoływana na podanym wskaźniku interfejsu w celu dopasowania do wywołania `Release` , które pojawi się, gdy `_variant_t` obiekt zostanie zniszczony. Jest to możliwe do wywołania `Release` na podanym wskaźniku interfejsu. Jeśli `fAddRef` jest **`false`** , ten Konstruktor przejmuje własność dostarczonego wskaźnika interfejsu; nie wywołuj do `Release` podanego wskaźnika interfejsu.

- **_variant_t (&dziesiętny ** `decSrc` **)** konstruuje `_variant_t` obiekt typu VT_DECIMAL z `DECIMAL` wartości.    

- **_variant_t (Byte** `bSrc` **)** konstruuje `_variant_t` obiekt typu `VT_UI1` z `BYTE` wartości.    

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Klasa _variant_t](../cpp/variant-t-class.md)
