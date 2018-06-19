---
title: _variant_t — ekstraktory | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 65049a473f62e728fcb4d74b581a08c0f1723fc9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32423321"
---
# <a name="variantt-extractors"></a>_variant_t — Ekstraktory
**Microsoft Specific**  
  
 Wyodrębnianie danych z hermetyzowany **VARIANT** obiektu.  
  
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
 Wyodrębnia nieprzetworzone dane z hermetyzowany **VARIANT**. Jeśli **VARIANT** nie jest jeszcze odpowiedniego typu **VariantChangeType** służy próby konwersji, i wygenerowaniu błędu, w przypadku awarii:  
  
-   **Operator (krótka)** wyodrębnia **krótki** wartości całkowitej.  
  
-   **Operator długi ()** wyodrębnia **długi** wartości całkowitej.  
  
-   **Operator float ()** wyodrębnia **float** wartość liczbową.  
  
-   **Operator (dwa razy)** wyodrębnia **podwójne** wartości całkowitej.  
  
-   **Operator (CY)** wyodrębnia **CY** obiektu.  
  
-   **Operator bool ()** wyodrębnia `bool` wartość.  
  
-   **Operator (dziesiętne)** wyodrębnia **DZIESIĘTNĄ** wartość.  
  
-   **Operator (BYTE)** wyodrębnia **BAJTÓW** wartość.  
  
-   **Operator () _bstr_t** wyodrębnia ciąg, który jest hermetyzowany w `_bstr_t` obiektu.  
  
-   **Operator IDispatch\*()** wyodrębnia wskaźnik dispinterface z hermetyzowany **VARIANT**. `AddRef` wywoływana jest wynikowego wskaźnika, tak aby wywołać jest **wersji** jego zwolnienia.  
  
-   **Operator IUnknown\*()** wyodrębnia wskaźnika interfejsu COM z hermetyzowany **VARIANT**. `AddRef` wywoływana jest wynikowego wskaźnika, tak aby wywołać jest **wersji** jego zwolnienia.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_variant_t, klasa](../cpp/variant-t-class.md)
