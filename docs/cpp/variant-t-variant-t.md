---
title: _variant_t::_variant_t
ms.date: 11/04/2016
f1_keywords:
- _variant_t::_variant_t
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
ms.openlocfilehash: fff116ef04967a1887eaa075d92d3ea0283d5427
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187534"
---
# <a name="_variant_t_variant_t"></a>_variant_t::_variant_t

**Specyficzne dla firmy Microsoft**

Konstruuje obiekt `_variant_t`.

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
Obiekt `VARIANT`, który ma zostać skopiowany do nowego obiektu `_variant_t`.

*pVarSrc*<br/>
Wskaźnik do obiektu `VARIANT`, który ma zostać skopiowany do nowego obiektu `_variant_t`.

*var_t_Src*<br/>
Obiekt `_variant_t`, który ma zostać skopiowany do nowego obiektu `_variant_t`.

*fCopy*<br/>
W przypadku **wartości false**dostarczony obiekt `VARIANT` jest dołączany do nowego obiektu `_variant_t` bez tworzenia nowej kopii przez `VariantCopy`.

*ISrc, sSrc*<br/>
Wartość całkowita do skopiowania do nowego obiektu `_variant_t`.

*vtSrc*<br/>
`VARTYPE` dla nowego obiektu `_variant_t`.

*fltSrc, dblSrc*<br/>
Wartość liczbowa do skopiowania do nowego obiektu `_variant_t`.

*cySrc*<br/>
Obiekt `CY`, który ma zostać skopiowany do nowego obiektu `_variant_t`.

*bstrSrc*<br/>
Obiekt `_bstr_t`, który ma zostać skopiowany do nowego obiektu `_variant_t`.

*strSrc, wstrSrc*<br/>
Ciąg, który ma zostać skopiowany do nowego obiektu `_variant_t`.

*bSrc*<br/>
Wartość **logiczna** , która ma zostać skopiowana do nowego obiektu `_variant_t`.

*pIUknownSrc*<br/>
Wskaźnik interfejsu COM do obiektu VT_UNKNOWN, który ma być hermetyzowany do nowego obiektu `_variant_t`.

*pDispSrc*<br/>
Wskaźnik interfejsu COM do obiektu VT_DISPATCH, który ma być hermetyzowany do nowego obiektu `_variant_t`.

*decSrc*<br/>
Wartość `DECIMAL`, która ma zostać skopiowana do nowego obiektu `_variant_t`.

*bSrc*<br/>
Wartość `BYTE`, która ma zostać skopiowana do nowego obiektu `_variant_t`.

*cSrc*<br/>
Wartość **char** do skopiowania do nowego obiektu `_variant_t`.

*usSrc*<br/>
**Krótka wartość bez znaku** do skopiowania do nowego obiektu `_variant_t`.

*ulSrc*<br/>
Wartość **długa bez znaku** do skopiowania do nowego obiektu `_variant_t`.

*iSrc*<br/>
Wartość **int** , która ma zostać skopiowana do nowego obiektu `_variant_t`.

*uiSrc*<br/>
Wartość **int bez znaku** , która ma zostać skopiowana do nowego obiektu `_variant_t`.

*i8Src*<br/>
Wartość **__int64** , która ma zostać skopiowana do nowego obiektu `_variant_t`.

*ui8Src*<br/>
Wartość **__int64 bez znaku** , która ma zostać skopiowana do nowego obiektu `_variant_t`.

## <a name="remarks"></a>Uwagi

- **_variant_t ()** Konstruuje pusty obiekt `_variant_t`, `VT_EMPTY`.

- **_variant_t (wariant &**  *varSrc*  **)** Konstruuje obiekt `_variant_t` z kopii `VARIANT` obiektu. Typ Variant jest zachowywany.

- **_variant_t (wariant** <strong>\*</strong> *pVarSrc* **)** Konstruuje obiekt `_variant_t` z kopii `VARIANT` obiektu. Typ Variant jest zachowywany.

- **_variant_t (_variant_t &**  *var_t_Src*  **)** Konstruuje obiekt `_variant_t` z innego obiektu `_variant_t`. Typ Variant jest zachowywany.

- **_variant_t (wariant &** *varSrc* **, bool**`fCopy` **)** Konstruuje obiekt `_variant_t` z istniejącego obiektu `VARIANT`. Jeśli *fCopy* ma **wartość false**, obiekt **Variant** jest dołączany do nowego obiektu bez tworzenia kopii.

- **_variant_t (Short***sSrc* **, VARTYPE**`vtSrc` **= VT_I2)** Konstruuje obiekt `_variant_t` typu VT_I2 lub VT_BOOL ze **skróconej** wartości całkowitej. Wszystkie inne `VARTYPE` są wynikiem E_INVALIDARG błędu.

- **_variant_t (long**`lSrc` **, VARTYPE**`vtSrc` **= VT_I4)** Konstruuje obiekt `_variant_t` typu VT_I4, VT_BOOL lub VT_ERROR z wartości **Long** Integer. Wszystkie inne `VARTYPE` są wynikiem E_INVALIDARG błędu.

- **_variant_t (float**`fltSrc` **)** Konstruuje obiekt `_variant_t` typu VT_R4 z wartości liczbowej **zmiennoprzecinkowej** .

- **_variant_t (double**`dblSrc` **, VARTYPE**`vtSrc` **= VT_R8)** Konstruuje obiekt `_variant_t` typu VT_R8 lub VT_DATE z **podwójnej** wartości liczbowej. Wszystkie inne `VARTYPE` są wynikiem E_INVALIDARG błędu.

- **_variant_t (CY &** `cySrc` **)** Konstruuje obiekt `_variant_t` typu VT_CY z obiektu `CY`.

- **_variant_t (_bstr_t &** `bstrSrc` **)** Konstruuje obiekt `_variant_t` typu VT_BSTR z obiektu `_bstr_t`. Przydzielono nowy `BSTR`.

- **_variant_t (wchar_t** <strong>\*</strong> *wstrSrc*  **)** Konstruuje obiekt `_variant_t` typu VT_BSTR z ciągu Unicode. Przydzielono nowy `BSTR`.

- **_variant_t (znak** <strong>\*</strong>`strSrc` **)** Konstruuje obiekt `_variant_t` typu VT_BSTR z ciągu. Przydzielono nowy `BSTR`.

- **_variant_t (** `bSrc`bool **)** Konstruuje obiekt `_variant_t` typu VT_BOOL z wartości **logicznej** .

- **_variant_t (IUnknown** <strong>\*</strong>`pIUknownSrc` **, bool**`fAddRef` **= true)** Konstruuje obiekt `_variant_t` typu VT_UNKNOWN ze wskaźnika interfejsu COM. Jeśli `fAddRef` ma **wartość true**, wówczas `AddRef` jest wywoływana na podanym wskaźniku interfejsu w celu dopasowania do wywołania `Release`, które nastąpi, gdy obiekt `_variant_t` zostanie zniszczony. Jest to możliwe do wywołania `Release` na podanym wskaźniku interfejsu. Jeśli `fAddRef` ma **wartość false**, ten Konstruktor przejmuje własność podanego wskaźnika interfejsu; Nie wywołuj `Release` na podanym wskaźniku interfejsu.

- **_variant_t (interfejs IDispatch** <strong>\*</strong>`pDispSrc` **, bool**`fAddRef` **= true)** Konstruuje obiekt `_variant_t` typu VT_DISPATCH ze wskaźnika interfejsu COM. Jeśli `fAddRef` ma **wartość true**, wówczas `AddRef` jest wywoływana na podanym wskaźniku interfejsu w celu dopasowania do wywołania `Release`, które nastąpi, gdy obiekt `_variant_t` zostanie zniszczony. Jest to możliwe do wywołania `Release` na podanym wskaźniku interfejsu. Jeśli `fAddRef` ma **wartość false**, ten Konstruktor przejmuje własność podanego wskaźnika interfejsu; Nie wywołuj `Release` na podanym wskaźniku interfejsu.

- **_variant_t (&AMP; dziesiętna**`decSrc` **)** Konstruuje obiekt `_variant_t` typu VT_DECIMAL z wartości `DECIMAL`.

- **_variant_t (bajt**`bSrc` **)** Konstruuje obiekt `_variant_t` typu `VT_UI1` z wartości `BYTE`.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_variant_t, klasa](../cpp/variant-t-class.md)
