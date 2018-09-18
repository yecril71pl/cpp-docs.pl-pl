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
ms.openlocfilehash: 66999d99e7809a3588dc3c92cae822bb4295ee07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073359"
---
# <a name="ifnotexists-statement"></a>__if_not_exists — Instrukcja

**__If_not_exists** instrukcji sprawdza, czy istnieje określony identyfikator. Jeśli identyfikator nie istnieje, jest wykonywany blok określonej instrukcji.

## <a name="syntax"></a>Składnia

```
__if_not_exists ( identifier ) { 
statements
};
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Identyfikator*|Identyfikator, którego istnienie, którą chcesz przetestować.|
|*Instrukcje*|Jedna lub więcej instrukcji do wykonania, jeśli *identyfikator* nie istnieje.|

## <a name="remarks"></a>Uwagi

> [!CAUTION]
>  Aby uzyskać najbardziej niezawodnym wyniki, użyj **__if_not_exists** instrukcji w następujące ograniczenia.

- Zastosuj **__if_not_exists** instrukcję, aby tylko proste typy, nie szablonów.

- Zastosuj **__if_not_exists** instrukcję, aby identyfikatory wewnątrz lub na zewnątrz klasy. Nie stosuj **__if_not_exists** instrukcji do zmiennych lokalnych.

- Użyj **__if_not_exists** oświadczenie tylko w treści funkcji. Poza treści funkcji **__if_not_exists** instrukcji można przetestować tylko do typów w pełni zdefiniowana.

- Podczas testowania dla przeciążonych funkcji nie można przetestować określonej formy przeciążenia.

To uzupełnienie **__if_not_exists** instrukcja jest [__if_exists](../cpp/if-exists-statement.md) instrukcji.

## <a name="example"></a>Przykład

Na przykład o tym, jak używać **__if_not_exists**, zobacz [__if_exists — instrukcja](../cpp/if-exists-statement.md).

## <a name="see-also"></a>Zobacz także

[Instrukcje wyboru](../cpp/selection-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[__if_exists, instrukcja](../cpp/if-exists-statement.md)