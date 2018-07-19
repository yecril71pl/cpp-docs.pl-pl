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
ms.openlocfilehash: fb2e870c7418c0d0a6cf3cd82bc0a8acb45466a0
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941268"
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
 *S1*  
 A `_bstr_t` kopiowanego obiektu.  
  
 *S2*  
 Ciąg znaków wielobajtowych.  
  
 *S3*  
 Ciąg Unicode  
  
 *var*  
 A [_variant_t](../cpp/variant-t-class.md) obiektu.  
  
 *BSTR*  
 Istniejące `BSTR` obiektu.  
  
 *fCopy*  
 W przypadku wartości FAŁSZ *bstr* argument jest dołączony do nowego obiektu bez skopiowanie przez wywołanie metody `SysAllocString`.  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli opisano `_bstr_t` konstruktorów.  
  
|Konstruktor|Opis|  
|-----------------|-----------------|  
|`_bstr_t( )`|Tworzy domyślny `_bstr_t` obiekt, który hermetyzuje wartość null `BSTR` obiektu.|  
|`_bstr_t( _bstr_t&`  `s1`  `)`|Konstruuje `_bstr_t` obiektu jako kopię innej.<br /><br /> Jest to *płytka* kopia, która zwiększa liczbę odwołań z zhermetyzowany `BSTR` obiektu zamiast tworzenia nowej.|  
|`_bstr_t( char*`  `s2`  `)`|Konstruuje `_bstr_t` obiektu przez wywołanie metody `SysAllocString` do tworzenia nowego `BSTR` obiektu, a następnie zamyka go.<br /><br /> Ten konstruktor wykonuje najpierw wielobajtowych do konwersji z Unicode.|  
|`_bstr_t( wchar_t*`  `s3`  `)`|Konstruuje `_bstr_t` obiektu przez wywołanie metody `SysAllocString` do tworzenia nowego `BSTR` obiektu, a następnie zamyka go.|  
|`_bstr_t( _variant_t&`  `var`  `)`|Konstruuje `_bstr_t` obiektu z `_variant_t` obiektu przez pobranie pierwszy `BSTR` obiektu z zhermetyzowanego obiektu VARIANT.|  
|`_bstr_t( BSTR`  `bstr` `, bool`  `fCopy`  `)`|Konstruuje `_bstr_t` obiektu z istniejącego `BSTR` (w przeciwieństwie do `wchar_t*` ciągu). Jeśli `fCopy` ma wartość FAŁSZ, podane `BSTR` jest dołączony do nowego obiektu bez wprowadzania nowej kopii z `SysAllocString`.<br /><br /> Ten konstruktor jest używany przez funkcje otoki w nagłówkach biblioteki typów do hermetyzacji i przejęcie na własność `BSTR` zwracanym przez metodę interfejsu.|  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_bstr_t — klasa](../cpp/bstr-t-class.md)   
 [_variant_t, klasa](../cpp/variant-t-class.md)