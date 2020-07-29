---
title: _variant_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _variant_t::operator=
helpviewer_keywords:
- operator= [C++], variant
- operator = [C++], variant
- = operator [C++], with specific Visual C++ objects
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
ms.openlocfilehash: 2db26a378526cd5f48992cb32ea46e9677125e66
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226961"
---
# <a name="_variant_toperator-"></a>_variant_t::operator =

**Specyficzne dla firmy Microsoft**

## <a name="syntax"></a>Składnia

```
_variant_t& operator=(
   const VARIANT& varSrc
);

_variant_t& operator=(
   const VARIANT* pVarSrc
);

_variant_t& operator=(
   const _variant_t& var_t_Src
);

_variant_t& operator=(
   short sSrc
);

_variant_t& operator=(
   long lSrc
);

_variant_t& operator=(
   float fltSrc
);

_variant_t& operator=(
   double dblSrc
);

_variant_t& operator=(
   const CY& cySrc
);

_variant_t& operator=(
   const _bstr_t& bstrSrc
);

_variant_t& operator=(
   const wchar_t* wstrSrc
);

_variant_t& operator=(
   const char* strSrc
);

_variant_t& operator=(
   IDispatch* pDispSrc
);

_variant_t& operator=(
   bool bSrc
);

_variant_t& operator=(
   IUnknown* pSrc
);

_variant_t& operator=(
   const DECIMAL& decSrc
);

_variant_t& operator=(
   BYTE bSrc
);

_variant_t& operator=(
   char cSrc
);

_variant_t& operator=(
   unsigned short usSrc
);

_variant_t& operator=(
   unsigned long ulSrc
);

_variant_t& operator=(
   int iSrc
);

_variant_t& operator=(
   unsigned int uiSrc
);

_variant_t& operator=(
   __int64 i8Src
);

_variant_t& operator=(
   unsigned __int64 ui8Src
);
```

## <a name="remarks"></a>Uwagi

Operator przypisuje nową wartość do `_variant_t` obiektu:

- **operator = (**  *varSrc*  **)** Przypisuje istniejący element `VARIANT` do `_variant_t` obiektu.

- **operator = (**  *pVarSrc*  **)** Przypisuje istniejący element `VARIANT` do `_variant_t` obiektu.

- **operator = (**  *var_t_Src*  **)** Przypisuje istniejący `_variant_t` obiekt do `_variant_t` obiektu.

- **operator = (**  *sSrc*  **)** Przypisuje **`short`** wartość całkowitą do `_variant_t` obiektu.

- **operator = (** `lSrc` **)** przypisuje **`long`** wartość całkowitą do `_variant_t` obiektu.    

- **operator = (**  *fltSrc*  **)** Przypisuje **`float`** wartość liczbową do `_variant_t` obiektu.

- **operator = (**  *dblSrc*  **)** Przypisuje **`double`** wartość liczbową do `_variant_t` obiektu.

- **operator = (**  *cySrc*  **)** Przypisuje `CY` obiekt do `_variant_t` obiektu.

- **operator = (**  *bstrSrc*  **)** Przypisuje `BSTR` obiekt do `_variant_t` obiektu.

- **operator = (**  *wstrSrc*  **)** Przypisuje ciąg Unicode do `_variant_t` obiektu.

- **operator = (** `strSrc` **)** przypisuje ciąg wielobajtowy do `_variant_t` obiektu.    

- **operator = (** `bSrc` **)** przypisuje **`bool`** wartość do `_variant_t` obiektu.  

- **operator = (**  *pDispSrc*  **)** Przypisuje `VT_DISPATCH` obiekt do `_variant_t` obiektu.

- **operator = (**  *pIUnknownSrc*  **)** Przypisuje `VT_UNKNOWN` obiekt do `_variant_t` obiektu.

- **operator = (**  *decSrc*  **)** Przypisuje `DECIMAL` wartość do `_variant_t` obiektu.

- **operator = (** `bSrc` **)** przypisuje `BYTE` wartość do `_variant_t` obiektu.  

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Klasa _variant_t](../cpp/variant-t-class.md)
