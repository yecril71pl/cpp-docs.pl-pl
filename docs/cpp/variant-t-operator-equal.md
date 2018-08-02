---
title: _variant_t::operator = | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= [C++], variant
- operator = [C++], variant
- = operator [C++], with specific Visual C++ objects
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d757c645ae131b88ffb99e571d1e08214eda8129
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462868"
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
  
-   **Operator = (***varSrc***)** przypisuje istniejące `VARIANT` do `_variant_t` obiektu.  
  
-   **Operator = (***pVarSrc***)** przypisuje istniejące `VARIANT` do `_variant_t` obiektu.  
  
-   **Operator = (***var_t_Src***)** przypisuje istniejące `_variant_t` obiekt `_variant_t` obiektu.      
  
-   **Operator = (***sSrc***)** przypisuje **krótki** wartość całkowitą na `_variant_t` obiektu.  
  
-   **Operator = (**`lSrc`**)** przypisuje **długie** wartość całkowitą na `_variant_t` obiektu.  
  
-   **Operator = (***fltSrc***)** przypisuje **float** wartość liczbową celu `_variant_t` obiektu.  
  
-   **Operator = (***dblSrc***)** przypisuje **double** wartość liczbową celu `_variant_t` obiektu.  
  
-   **Operator = (***cySrc***)** przypisuje `CY` obiekt `_variant_t` obiektu.  
  
-   **Operator = (***bstrSrc***)** przypisuje `BSTR` obiekt `_variant_t` obiektu.  
  
-   **Operator = (***wstrSrc***)** przypisuje ciąg Unicode na `_variant_t` obiektu.  
  
-   **Operator = (**`strSrc`**)** przypisuje wielobajtowy ciąg do `_variant_t` obiektu.  
  
-   **Operator = (** `bSrc` **)** przypisuje **bool** wartość `_variant_t` obiektu.  
  
-   **Operator = (***pDispSrc***)** przypisuje `VT_DISPATCH` obiekt `_variant_t` obiektu.  
  
-   **Operator = (***pIUnknownSrc***)** przypisuje `VT_UNKNOWN` obiekt `_variant_t` obiektu.  
  
-   **Operator = (***decSrc***)** przypisuje `DECIMAL` wartość `_variant_t` obiektu.  
  
-   **Operator = (** `bSrc` **)** przypisuje `BYTE` wartość `_variant_t` obiektu.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [_variant_t, klasa](../cpp/variant-t-class.md)