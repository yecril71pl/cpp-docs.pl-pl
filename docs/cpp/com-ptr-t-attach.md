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
ms.openlocfilehash: f8e982ebd9a09d4dfcb5e4b5e150b42a1e8d5c75
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947936"
---
# <a name="comptrtattach"></a>_com_ptr_t::Attach
**Microsoft Specific**  
  
 Hermetyzuje surowego wskaźnika interfejsu tego inteligentnego wskaźnika typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
void Attach( Interface* pInterface ) throw( );  
void Attach( Interface* pInterface, bool fAddRef ) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 *pInterface*  
 Surowego wskaźnika interfejsu.  
  
 *fAddRef*  
 Jeśli ma wartość PRAWDA, następnie `AddRef` jest wywoływana. Jeśli wartość FAŁSZ, `_com_ptr_t` obiektu przejmuje na własność surowego wskaźnika interfejsu bez wywoływania `AddRef`.  
  
## <a name="remarks"></a>Uwagi  
  
-   **Dołącz (***pInterface***)** `AddRef` nie zostanie wywołana.     Własność interfejsu jest przekazywany do tego `_com_ptr_t` obiektu. `Release` jest wywoływana, aby zmniejszyć licznikiem odwołań do wcześniej zhermetyzowanego wskaźnika.  
  
-   **Dołącz (***pInterface* **,***fAddRef***)** Jeśli *fAddRef* ma wartość PRAWDA, `AddRef`jest wywoływana, aby zwiększyć licznik odwołań dla interfejsu zhermetyzowanego wskaźnika.       Jeśli *fAddRef* ma wartość FAŁSZ, to `_com_ptr_t` obiektu przejmuje na własność surowego wskaźnika interfejsu bez wywoływania `AddRef`. `Release` jest wywoływana, aby zmniejszyć licznikiem odwołań do wcześniej zhermetyzowanego wskaźnika.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)