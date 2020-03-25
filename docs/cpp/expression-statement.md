---
title: Instrukcja wyrażeń
ms.date: 11/04/2016
helpviewer_keywords:
- statements [C++], expression
- expression statements
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
ms.openlocfilehash: 2f12bbbafd9be50f851e36f472098431f9ac0d5d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189003"
---
# <a name="expression-statement"></a>Instrukcja wyrażeń

Instrukcje wyrażenia powodują, że wyrażenia mają być oceniane. Żaden transfer kontrolki lub iteracji nie ma miejsca w wyniku instrukcji wyrażenia.

Składnia instrukcji Expression jest po prostu

## <a name="syntax"></a>Składnia

```
[expression ] ;
```

## <a name="remarks"></a>Uwagi

Wszystkie wyrażenia w instrukcji wyrażenia są oceniane i wszystkie efekty uboczne są kończone przed wykonaniem następnej instrukcji. Najczęstsze instrukcje wyrażeń to przypisania i wywołania funkcji.  Ponieważ wyrażenie jest opcjonalne, sam średnik jest uznawany za pustą instrukcję wyrażenia, nazywaną instrukcją [null](../cpp/null-statement.md) .

## <a name="see-also"></a>Zobacz też

[Przegląd instrukcji C++](../cpp/overview-of-cpp-statements.md)
