---
title: _bstr_t::operator = | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43e28aa7d7b3682c45f4f8b7a94e990374d83b46
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947741"
---
# <a name="bstrtoperator-"></a>_bstr_t::operator =
**Microsoft Specific**  
  
 Przypisuje nową wartość do istniejącej `_bstr_t` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
_bstr_t& operator=(const _bstr_t& s1) throw ( );  
_bstr_t& operator=(const char* s2);  
_bstr_t& operator=(const wchar_t* s3);  
_bstr_t& operator=(const _variant_t& var);  
```  
  
#### <a name="parameters"></a>Parametry  
 *S1*  
 A `_bstr_t` obiekt ma być przypisane do istniejącej `_bstr_t` obiektu.  
  
 *S2*  
 Wielobajtowy ciąg ma być przypisane do istniejącej `_bstr_t` obiektu.  
  
 *S3*  
 Ciąg Unicode ma być przypisane do istniejącej `_bstr_t` obiektu.  
  
 *var*  
 A `_variant_t` obiekt ma być przypisane do istniejącej `_bstr_t` obiektu.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="example"></a>Przykład  
 Zobacz [_bstr_t::przypisanie](../cpp/bstr-t-assign.md) na przykład za pomocą **operator =**.  
  
## <a name="see-also"></a>Zobacz też  
 [_bstr_t, klasa](../cpp/bstr-t-class.md)