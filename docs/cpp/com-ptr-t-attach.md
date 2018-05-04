---
title: _com_ptr_t::Dołącz | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Attach
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7341695ad0cbc8384da859b80a72a63d8d52215f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="comptrtattach"></a>_com_ptr_t::Attach
**Microsoft Specific**  
  
 Hermetyzuje wskaźnik interfejsu pierwotnego, typu wskaźnika inteligentnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      void Attach(  
   Interface* pInterface   
) throw( );  
void Attach(  
   Interface* pInterface,  
   bool fAddRef   
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pInterface`  
 Wskaźnik interfejsu pierwotnego.  
  
 `fAddRef`  
 Jeśli jest **true**, następnie `AddRef` jest wywoływana. Jeśli jest **false**, `_com_ptr_t` obiektu przejmuje wskaźnik interfejsu pierwotnego, bez wywoływania elementu `AddRef`.  
  
## <a name="remarks"></a>Uwagi  
  
-   **Dołącz (**`pInterface`**)** `AddRef` nie jest wywoływany.     Własność interfejsu jest przekazywana do `_com_ptr_t` obiektu. **Wersja** jest wywoływana, aby zmniejszyć licznika odwołań do wcześniej hermetyzowany wskaźnika.  
  
-   **Dołącz (** `pInterface` **,**`fAddRef`**)** Jeśli `fAddRef` jest **true**, `AddRef` jest wywoływana, aby zwiększyć odwołania Liczba dla wskaźnika interfejsu hermetyzowany.       Jeśli `fAddRef` jest **false**, to `_com_ptr_t` obiektu przejmuje wskaźnik interfejsu pierwotnego, bez wywoływania elementu `AddRef`. **Wersja** jest wywoływana, aby zmniejszyć licznika odwołań do wcześniej hermetyzowany wskaźnika.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)