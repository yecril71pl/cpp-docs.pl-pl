---
title: _variant_t::operator = | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _variant_t::operator=
dev_langs: C++
helpviewer_keywords:
- operator= [C++], variant
- operator = [C++], variant
- = operator [C++], with specific Visual C++ objects
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 88998f18c750e064ee8eae254ca7ee4487be7176
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="varianttoperator-"></a>_variant_t::operator =
**Dotyczące firmy Microsoft**  
  
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
  
-   **Operator = (***varSrc***)** przypisuje istniejące **VARIANT** do `_variant_t` obiektu.  
  
-   **Operator = (***pVarSrc***)** przypisuje istniejące **VARIANT** do `_variant_t` obiektu.  
  
-   **Operator = (***var_t_Src***)** przypisuje istniejące `_variant_t` do obiektu `_variant_t` obiektu.  
  
-   **Operator = (***sSrc***)** przypisuje **krótki** wartość całkowitą `_variant_t` obiektu.  
  
-   **Operator = (**`lSrc`**)** przypisuje **długi** wartość całkowitą `_variant_t` obiektu.  
  
-   **Operator = (***fltSrc***)** przypisuje **float** wartość liczbową `_variant_t` obiektu.  
  
-   **Operator = (***dblSrc***)** przypisuje **podwójne** wartość liczbową `_variant_t` obiektu.  
  
-   **Operator = (***cySrc***)** przypisuje **CY** do obiektu `_variant_t` obiektu.  
  
-   **Operator = (***bstrSrc***)** przypisuje `BSTR` do obiektu `_variant_t` obiektu.  
  
-   **Operator = (***wstrSrc***)** przypisuje ciąg Unicode `_variant_t` obiektu.  
  
-   **Operator = (**`strSrc`**)** przypisuje wielobajtowe ciąg `_variant_t` obiektu.  
  
-   **Operator = (** `bSrc` **)** przypisuje `bool` do wartości `_variant_t` obiektu.  
  
-   **Operator = (***pDispSrc***)** przypisuje **VT_DISPATCH** do obiektu `_variant_t` obiektu.  
  
-   **Operator = (***pIUnknownSrc***)** przypisuje **VT_UNKNOWN** do obiektu `_variant_t` obiektu.  
  
-   **Operator = (***decSrc***)** przypisuje **DZIESIĘTNĄ** do wartości `_variant_t` obiektu.  
  
-   **Operator = (** `bSrc` **)** przypisuje **BAJTÓW** do wartości `_variant_t` obiektu.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_variant_t, klasa](../cpp/variant-t-class.md)