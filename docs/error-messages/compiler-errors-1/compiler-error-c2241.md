---
title: Błąd kompilatora C2241 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2241
dev_langs:
- C++
helpviewer_keywords:
- C2241
ms.assetid: 2f4e2c2c-b95c-4afe-bbe0-4214cd39d140
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd97551e0feaecce776cc552353716c67822f273
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055900"
---
# <a name="compiler-error-c2241"></a>Błąd kompilatora C2241

'Identyfikator': dostęp do składowej jest ograniczony

Kod próbuje uzyskać dostępu do członka prywatnych lub chronionych.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem, korzystając z poniższymi możliwymi rozwiązaniami

1. Zmień poziom dostępu elementu członkowskiego.

1. Deklaruje składowej `friend` uzyskiwania dostępu do funkcji.