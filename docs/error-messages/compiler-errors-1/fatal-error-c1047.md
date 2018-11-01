---
title: Błąd krytyczny C1047
ms.date: 11/04/2016
f1_keywords:
- C1047
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
ms.openlocfilehash: 053c4d828b3583d0e16ab8f4fe03a4b0bbed96f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663197"
---
# <a name="fatal-error-c1047"></a>Błąd krytyczny C1047

Plik obiektu lub biblioteki 'Plik' został utworzony za pomocą starszego kompilatora niż inne obiekty; Przebuduj stare obiekty i biblioteki

C1047 jest przyczyną plików obiektów i bibliotek są tworzone za pomocą **opcję/LTCG** są połączone ze sobą, ale których tych plików obiektu lub bibliotek są tworzone z użyciem różnych wersji narzędzi Visual C++.

Może to nastąpić, jeśli rozpocząć korzystanie z nowej wersji kompilatora, ale nie wykonuj czystego ponownego kompilowania istniejących plików obiektów i bibliotek.

Aby rozwiązać C1047, Odbuduj wszystkich plików obiektu i bibliotek.