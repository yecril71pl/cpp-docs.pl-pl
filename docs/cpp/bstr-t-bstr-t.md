---
title: _bstr_t::_bstr_t | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::_bstr_t
dev_langs:
- C++
helpviewer_keywords:
- BSTR object
- _bstr_t method [C++]
- _bstr_t class
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 824108b78ede3999a83b1c7c1ac75cc847f182f5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="bstrtbstrt"></a>_bstr_t::_bstr_t
**Microsoft Specific**  
  
 Konstruuje `_bstr_t` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
_bstr_t( ) throw( );   
_bstr_t(  
   const _bstr_t& s1   
) throw( );  
_bstr_t(  
   const char* s2   
);  
_bstr_t(  
   const wchar_t* s3   
);  
_bstr_t(  
   const _variant_t& var   
);  
_bstr_t(  
   BSTR bstr,  
   bool fCopy   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `s1`  
 A `_bstr_t` obiektu do skopiowania.  
  
 `s2`  
 Ciąg znaków wielobajtowych.  
  
 `s3`  
 Ciąg Unicode  
  
 `var`  
 A [_variant_t](../cpp/variant-t-class.md) obiektu.  
  
 `bstr`  
 Istniejące `BSTR` obiektu.  
  
 `fCopy`  
 Jeśli `false`, `bstr` argument jest dołączony do nowego obiektu bez tworzenia kopii przez wywołanie metody `SysAllocString`.  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli opisano `_bstr_t` konstruktorów.  
  
|Konstruktor|Opis|  
|-----------------|-----------------|  
|`_bstr_t( )`|Tworzy domyślny `_bstr_t` obiekt hermetyzujący wartość null `BSTR` obiektu.|  
|`_bstr_t( _bstr_t&`  `s1`  `)`|Konstruuje `_bstr_t` obiektu jest kopią innego.<br /><br /> Jest to *skrócona* kopia, co zwiększa liczbę odwołanie z hermetyzowany `BSTR` obiektu zamiast tworzenia nowej.|  
|`_bstr_t( char*`  `s2`  `)`|Konstruuje `_bstr_t` obiektu przez wywołanie metody `SysAllocString` do tworzenia nowego `BSTR` obiekt, a następnie zamyka go.<br /><br /> Ten konstruktor najpierw jest przeprowadzane wielobajtowe do konwersji Unicode.|  
|`_bstr_t( wchar_t*`  `s3`  `)`|Konstruuje `_bstr_t` obiektu przez wywołanie metody `SysAllocString` do tworzenia nowego `BSTR` obiekt, a następnie zamyka go.|  
|`_bstr_t( _variant_t&`  `var`  `)`|Konstruuje `_bstr_t` obiekt z `_variant_t` obiektu przez pobranie pierwszy `BSTR` obiektu z obiektu hermetyzowany VARIANT.|  
|`_bstr_t( BSTR`  `bstr` `, bool`  `fCopy`  `)`|Konstruuje `_bstr_t` obiektu z istniejącego `BSTR` (w przeciwieństwie do `wchar_t*` ciągu). Jeśli `fCopy` ma wartość false, podane `BSTR` jest dołączony do nowego obiektu bez tworzenia nowej kopii z `SysAllocString`.<br /><br /> Ten konstruktor jest używany przez funkcje otoki w nagłówkach biblioteki typu do Hermetyzowanie i przejąć na własność `BSTR` który jest zwracany przez metodę interfejsu.|  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_bstr_t — klasa](../cpp/bstr-t-class.md)   
 [_variant_t, klasa](../cpp/variant-t-class.md)