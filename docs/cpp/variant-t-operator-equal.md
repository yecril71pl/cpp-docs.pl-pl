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
ms.openlocfilehash: 6a8f31e8db6f5ca5a680dd47b5d5391c84ce5025
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403324"
---
# <a name="varianttoperator-"></a>_variant_t::operator =

**Microsoft Specific**

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

- **Operator = (***varSrc***)** przypisuje istniejące `VARIANT` do `_variant_t` obiektu.

- **Operator = (***pVarSrc***)** przypisuje istniejące `VARIANT` do `_variant_t` obiektu.

- **Operator = (***var_t_Src***)** przypisuje istniejące `_variant_t` obiekt `_variant_t` obiektu.    

- **Operator = (***sSrc***)** przypisuje **krótki** wartość całkowitą na `_variant_t` obiektu.

- **Operator = (**`lSrc`**)** przypisuje **długie** wartość całkowitą na `_variant_t` obiektu.

- **Operator = (***fltSrc***)** przypisuje **float** wartość liczbową celu `_variant_t` obiektu.

- **Operator = (***dblSrc***)** przypisuje **double** wartość liczbową celu `_variant_t` obiektu.

- **Operator = (***cySrc***)** przypisuje `CY` obiekt `_variant_t` obiektu.

- **Operator = (***bstrSrc***)** przypisuje `BSTR` obiekt `_variant_t` obiektu.

- **Operator = (***wstrSrc***)** przypisuje ciąg Unicode na `_variant_t` obiektu.

- **Operator = (**`strSrc`**)** przypisuje wielobajtowy ciąg do `_variant_t` obiektu.

- **Operator = (** `bSrc` **)** przypisuje **bool** wartość `_variant_t` obiektu.

- **Operator = (***pDispSrc***)** przypisuje `VT_DISPATCH` obiekt `_variant_t` obiektu.

- **Operator = (***pIUnknownSrc***)** przypisuje `VT_UNKNOWN` obiekt `_variant_t` obiektu.

- **Operator = (***decSrc***)** przypisuje `DECIMAL` wartość `_variant_t` obiektu.

- **Operator = (** `bSrc` **)** przypisuje `BYTE` wartość `_variant_t` obiektu.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_variant_t, klasa](../cpp/variant-t-class.md)