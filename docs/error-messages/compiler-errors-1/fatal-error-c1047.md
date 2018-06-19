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
ms.openlocfilehash: ce88321173ee2c8cc286f18d8ab8f1bf5ec98e13
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198628"
---
# <a name="fatal-error-c1047"></a>Błąd krytyczny C1047
Plik obiektu lub biblioteki 'Plik' został utworzony za pomocą starszego kompilatora niż inne obiekty; Przebuduj stare obiekty i biblioteki  
  
 C1047 występuje po plików obiektu i bibliotek skompilowanej za pomocą **opcję/LTCG** są połączone ze sobą, lecz których tych plików obiektu i bibliotek są tworzone różne wersje zestawu narzędzi Visual C++.  
  
 Może to się zdarzyć, jeśli rozpocząć korzystanie z nowej wersji kompilatora, ale nie czystą kompilowania istniejących plików obiektu i bibliotek.  
  
 Aby rozwiązać C1047, Odbuduj wszystkich plików obiektu i bibliotek.