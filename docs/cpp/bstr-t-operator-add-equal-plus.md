---
title: _bstr_t::operator += + | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
dev_langs:
- C++
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e443b233e19f6cdc64d7d6021a9a9c078a4f327
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="bstrtoperator--"></a>_bstr_t::operator +=, +
**Microsoft Specific**  
  
 Dołącza znaki na końcu `_bstr_t` obiektu lub łączy dwa ciągi.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      _bstr_t& operator+=(  
   const _bstr_t& s1   
);  
_bstr_t operator+(  
   const _bstr_t& s1   
);  
friend _bstr_t operator+(  
   const char* s2,  
   const _bstr_t& s1   
);  
friend _bstr_t operator+(  
   const wchar_t* s3,  
   const _bstr_t& s1   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *S1*  
 A `_bstr_t` obiektu.  
  
 *S2*  
 Ciąg znaków wielobajtowych.  
  
 `s3`  
 Ciąg Unicode.  
  
## <a name="remarks"></a>Uwagi  
 Tych operatorów należy wykonać ciągów:  
  
-   **Operator += (***s1***)** dołącza znaków w hermetyzowany `BSTR` z *s1* na końcu tego obiektu hermetyzowany `BSTR`.      
  
-   **Operator + (***s1***)** zwraca nowy `_bstr_t` który jest tworzony przez łączenie tego obiektu `BSTR` z tymi, które *s1*.      
  
-   **Operator + (***s2***&#124;***s1***)** zwraca nową `_bstr_t` który jest tworzony przez łączenie ciąg znaków wielobajtowych *s2*konwersji na format Unicode, z `BSTR` hermetyzowane w *s1*.          
  
-   **Operator + (** `s3` **,***s1***)** zwraca nową `_bstr_t` który jest tworzony przez łączenie ciągów Unicode `s3` z `BSTR` hermetyzowane w *s1*.        
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_bstr_t, klasa](../cpp/bstr-t-class.md)