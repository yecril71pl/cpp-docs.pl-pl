---
title: Błąd kompilatora C3552 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3552
dev_langs:
- C++
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd9f7ae37500e115fa33fa61298cab800c88f9c7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081263"
---
# <a name="compiler-error-c3552"></a>Błąd kompilatora C3552

"typename": koniec określony typ zwracany nie może zawierać "auto"

Jeśli używasz `auto` słowa kluczowego jako symbol zastępczy dla zwracanego typu funkcji, musisz podać późno określony typ zwracany. Jednak nie można użyć innego `auto` słów kluczowych do określania późno zdefiniowanym typem zwracanym. Na przykład poniższy fragment kodu powoduje błąd C3552.

`auto myFunction->auto; // C3552`