---
title: Błąd krytyczny C1047 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1047
dev_langs:
- C++
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1983fa0a18667d98f84dfe5049afd4e872d87d93
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021593"
---
# <a name="fatal-error-c1047"></a>Błąd krytyczny C1047

Plik obiektu lub biblioteki 'Plik' został utworzony za pomocą starszego kompilatora niż inne obiekty; Przebuduj stare obiekty i biblioteki

C1047 jest przyczyną plików obiektów i bibliotek są tworzone za pomocą **opcję/LTCG** są połączone ze sobą, ale których tych plików obiektu lub bibliotek są tworzone z użyciem różnych wersji narzędzi Visual C++.

Może to nastąpić, jeśli rozpocząć korzystanie z nowej wersji kompilatora, ale nie wykonuj czystego ponownego kompilowania istniejących plików obiektów i bibliotek.

Aby rozwiązać C1047, Odbuduj wszystkich plików obiektu i bibliotek.