---
title: __if_not_exists — instrukcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __if_not_exists_cpp
dev_langs:
- C++
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd4e586a211d7c4e2ead1ce3f225e2d92d2bd5a7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
 [Keywords](../cpp/keywords-cpp.md)   
 [__if_exists, instrukcja](../cpp/if-exists-statement.md)