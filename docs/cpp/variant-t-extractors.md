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
ms.openlocfilehash: 3a8480a645728808ef4eae7a42c5080313d9fc6f
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940348"
---
# <a name="variantt-extractors"></a>_variant_t — Ekstraktory
**Microsoft Specific**  
  
 Wyodrębnianie danych z zhermetyzowany `VARIANT` obiektu.  
  
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
 Wyodrębnia dane pierwotne z zhermetyzowany `VARIANT`. Jeśli `VARIANT` nie jest jeszcze odpowiedniego typu `VariantChangeType` służy do próba konwersji i zostanie wygenerowany błąd w przypadku niepowodzenia:  
  
-   **krótki () — operator** wyodrębnia **krótki** wartość całkowitą.  
  
-   **długi () — operator** wyodrębnia **długie** wartość całkowitą.  
  
-   **Operator float ()** wyodrębnia **float** wartość liczbową.  
  
-   **double () — operator** wyodrębnia **double** wartość całkowitą.  
  
-   **Operator () CY** wyodrębnia `CY` obiektu.  
  
-   **(operator bool)** wyodrębnia **bool** wartość.  
  
-   **Operator (dziesiętna)** wyodrębnia `DECIMAL` wartość.  
  
-   **Operator (BAJTÓW)** wyodrębnia `BYTE` wartość.  
  
-   **Operator () z _bstr_t** wyodrębnia ciąg, który jest hermetyzowany w `_bstr_t` obiektu.  
  
-   **Operator IDispatch\*()** wyodrębnia wskaźnik dispinterface z zhermetyzowany `VARIANT`. `AddRef` jest wywoływana w wskaźnik wynikowy, tak aby wywołać to `Release` zwolnienie go.  
  
-   **Operator IUnknown\*()** wyodrębnia wskaźnika interfejsu COM z zhermetyzowany `VARIANT`. `AddRef` jest wywoływana w wskaźnik wynikowy, tak aby wywołać to `Release` zwolnienie go.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_variant_t, klasa](../cpp/variant-t-class.md)
