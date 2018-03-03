---
title: "__if_not_exists — instrukcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __if_not_exists_cpp
dev_langs:
- C++
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2342354528811f415a9c9aeb819e2c0e7cec6646
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ifnotexists-statement"></a>__if_not_exists — Instrukcja
`__if_not_exists` Instrukcji sprawdza, czy istnieje określony identyfikator. Jeśli identyfikator nie istnieje, jest wykonywany bloku instrukcję.  
  
## <a name="syntax"></a>Składnia  
  
```  
__if_not_exists ( identifier ) {   
statements  
};  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`identifier`|Identyfikator istnienia, którego chcesz przetestować.|  
|`statements`|Co najmniej jeden instrukcje do wykonania, gdy `identifier` nie istnieje.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!CAUTION]
>  Aby osiągnąć najbardziej niezawodnym wyniki, należy użyć `__if_not_exists` zgodnie z następującymi ograniczeniami.  
  
-   Zastosuj `__if_not_exists` oświadczenie tylko proste typy, nie szablonów.  
  
-   Zastosuj `__if_not_exists` instrukcji do identyfikatorów wewnątrz lub na zewnątrz klasy. Nie stosuj `__if_not_exists` instrukcji do zmiennych lokalnych.  
  
-   Użyj `__if_not_exists` oświadczenie tylko w treści funkcji. Poza treści funkcji `__if_not_exists` instrukcji można przetestować tylko w pełni zdefiniowanych typów.  
  
-   Podczas testowania dla przeciążonej funkcji nie można przetestować wykonania określonej formy przeciążenia.  
  
 Uzupełnienie `__if_not_exists` instrukcja jest [__if_exists](../cpp/if-exists-statement.md) instrukcji.  
  
## <a name="example"></a>Przykład  
 Na przykład o sposobie używania `__if_not_exists`, zobacz [__if_exists — instrukcja](../cpp/if-exists-statement.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zaznaczenie — instrukcje](../cpp/selection-statements-cpp.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [__if_exists, instrukcja](../cpp/if-exists-statement.md)