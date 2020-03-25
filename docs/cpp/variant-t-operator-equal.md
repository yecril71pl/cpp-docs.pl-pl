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
ms.openlocfilehash: 402251592a87b723d75fd1b2cd0786be7b17dbfc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187625"
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

Operator przypisuje nową wartość do obiektu `_variant_t`:

- **operator = (**  *varSrc*  **)** Przypisuje istniejące `VARIANT` do obiektu `_variant_t`.

- **operator = (**  *pVarSrc*  **)** Przypisuje istniejące `VARIANT` do obiektu `_variant_t`.

- **operator = (**  *var_t_Src*  **)** Przypisuje istniejący obiekt `_variant_t` do obiektu `_variant_t`.

- **operator = (**  *sSrc*  **)** Przypisuje **krótką** wartość całkowitą do obiektu `_variant_t`.

- **operator = (** `lSrc` **)** Przypisuje wartość **Long** Integer do obiektu `_variant_t`.

- **operator = (**  *fltSrc*  **)** Przypisuje wartość liczbową **zmiennoprzecinkową** do obiektu `_variant_t`.

- **operator = (**  *dblSrc*  **)** Przypisuje **podwójną** wartość liczbową do obiektu `_variant_t`.

- **operator = (**  *cySrc*  **)** Przypisuje obiekt `CY` do `_variant_t` obiektu.

- **operator = (**  *bstrSrc*  **)** Przypisuje obiekt `BSTR` do `_variant_t` obiektu.

- **operator = (**  *wstrSrc*  **)** Przypisuje ciąg Unicode do obiektu `_variant_t`.

- **operator = (** `strSrc` **)** Przypisuje ciąg wielobajtowy do obiektu `_variant_t`.

- **operator = (** `bSrc` **)** Przypisuje wartość **logiczną** do obiektu `_variant_t`.

- **operator = (**  *pDispSrc*  **)** Przypisuje obiekt `VT_DISPATCH` do `_variant_t` obiektu.

- **operator = (**  *pIUnknownSrc*  **)** Przypisuje obiekt `VT_UNKNOWN` do `_variant_t` obiektu.

- **operator = (**  *decSrc*  **)** Przypisuje wartość `DECIMAL` do obiektu `_variant_t`.

- **operator = (** `bSrc` **)** Przypisuje wartość `BYTE` do obiektu `_variant_t`.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_variant_t, klasa](../cpp/variant-t-class.md)
