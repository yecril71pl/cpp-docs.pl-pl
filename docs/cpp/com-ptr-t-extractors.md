---
title: _com_ptr_t — ekstraktory | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::operatorInterface&
- _com_ptr_t::operatorbool
- _com_ptr_t::operator->
- _com_ptr_t::operator*
dev_langs:
- C++
helpviewer_keywords:
- operator Interface& [C++]
- '* operator [C++], with specific objects'
- operator& [C++]
- operator* [C++]
- -> operator [C++], with specific objects
- '& operator [C++], with specific objects'
- operator Interface* [C++]
- operator * [C++]
- operator->
- operator bool
- extractors, _com_ptr_t class
- extractors [C++]
ms.assetid: 194b9e0e-123c-49ff-a187-0a7fcd68145a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1343d7dd5f6a35bb222b731294ec897116b9e4b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="comptrt-extractors"></a>_com_ptr_t — Ekstraktory
**Microsoft Specific**  
  
 Wyodrębnij hermetyzowany wskaźnika interfejsu COM.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      operator Interface*( ) const throw( );   
operator Interface&( ) const;   
Interface& operator*( ) const;   
Interface* operator->( ) const;   
Interface** operator&( ) throw( );   
operator bool( ) const throw( );  
```  
  
## <a name="remarks"></a>Uwagi  
  
-   **Operator interfejsu\***  zwraca wskaźnik zhermetyzowany interfejs, który może być **NULL**.  
  
-   **Operator interfejsu &** zwraca odwołanie do wskaźnika interfejsu hermetyzowany i generuje błąd, jeśli wskaźnik jest **NULL**.  
  
-   **operator\***  umożliwia działa tak, jakby była to rzeczywista interfejsu hermetyzowany podczas wyłuskiwany obiekt wskaźnika inteligentnego.  
  
-   **operator ->** umożliwia działa tak, jakby była to rzeczywista interfejsu hermetyzowany podczas wyłuskiwany obiekt wskaźnika inteligentnego.  
  
-   **Operator &** zwalnia wszelkie wskaźnika zhermetyzowany interfejs, zastępuje go tekstem **NULL**i zwraca adres hermetyzowany wskaźnika. Dzięki temu wskaźnika inteligentnego, należy przesłać za pomocą adresu funkcji, które ma **limit** parametru za pomocą którego zwraca wskaźnika interfejsu.  
  
-   **Operator bool** umożliwia obiekt wskaźnika inteligentnego do użycia w wyrażeniu warunkowym. Ten operator zwraca **true** Jeśli wskaźnik jest nie **NULL**.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)