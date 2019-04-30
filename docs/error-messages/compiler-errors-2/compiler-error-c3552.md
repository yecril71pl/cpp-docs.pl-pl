---
title: Błąd kompilatora C3552
ms.date: 11/04/2016
f1_keywords:
- C3552
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
ms.openlocfilehash: 27c4707097f43266a3be57ad6dc9591ab6f34e97
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375941"
---
# <a name="compiler-error-c3552"></a>Błąd kompilatora C3552

"typename": koniec określony typ zwracany nie może zawierać "auto"

Jeśli używasz `auto` słowa kluczowego jako symbol zastępczy dla zwracanego typu funkcji, musisz podać późno określony typ zwracany. Jednak nie można użyć innego `auto` słów kluczowych do określania późno zdefiniowanym typem zwracanym. Na przykład poniższy fragment kodu powoduje błąd C3552.

`auto myFunction->auto; // C3552`