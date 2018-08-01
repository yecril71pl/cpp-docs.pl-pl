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
ms.openlocfilehash: aad73939b8fd011fd6e1c9bf16f8dfe6eb303ff3
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405746"
---
# <a name="bstrtoperator--"></a>_bstr_t::operator +=, +
**Microsoft Specific**  
  
 Dołącza znaki do końca `_bstr_t` obiektu lub łączy dwa ciągi.  
  
## <a name="syntax"></a>Składnia  
  
```  
_bstr_t& operator+=( const _bstr_t& s1 );  
_bstr_t operator+( const _bstr_t& s1 );  
friend _bstr_t operator+( const char* s2, const _bstr_t& s1);  
friend _bstr_t operator+( const wchar_t* s3, const _bstr_t& s1);  
```  
  
#### <a name="parameters"></a>Parametry  
 *S1*  
 Element `_bstr_t` obiektu.  
  
 *S2*  
 Ciąg znaków wielobajtowych.  
  
 *S3*  
 Ciąg Unicode.  
  
## <a name="remarks"></a>Uwagi  
 Te operatory wykonaj ciągów:  
  
-   **+= — Operator (***s1***)** dołącza znaki w zhermetyzowany `BSTR` z *s1* na końcu tego obiektu zhermetyzowany`BSTR`.  
  
-   **Operator + (***s1***)** zwraca nową `_bstr_t` , jest tworzona przez złączenie tego obiektu `BSTR` z tymi, które *s1*.  
  
-   **Operator + (***s2***&#124;***s1***)** zwraca nowy `_bstr_t` , jest tworzona przez złączenie ciąg znaków wielobajtowych *s2*, przekonwertowane na format Unicode, za pomocą `BSTR` hermetyzowane w *s1*.          
  
-   **Operator + (***s3* **,***s1***)** zwraca nowy `_bstr_t` , jest tworzona przez złączenie ciąg Unicode *s3* z `BSTR` hermetyzowane w *s1*.        
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [_bstr_t, klasa](../cpp/bstr-t-class.md)