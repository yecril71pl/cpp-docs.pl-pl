---
title: "Błąd krytyczny C1047 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1047
dev_langs: C++
helpviewer_keywords: C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b848f874f382e3d4f944a7eb372db9dcc5011f59
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1047"></a>Błąd krytyczny C1047
Plik obiektu lub biblioteki 'Plik' został utworzony za pomocą starszego kompilatora niż inne obiekty; Przebuduj stare obiekty i biblioteki  
  
 C1047 występuje po plików obiektu i bibliotek skompilowanej za pomocą **opcję/LTCG** są połączone ze sobą, lecz których tych plików obiektu i bibliotek są tworzone różne wersje zestawu narzędzi Visual C++.  
  
 Może to się zdarzyć, jeśli rozpocząć korzystanie z nowej wersji kompilatora, ale nie czystą kompilowania istniejących plików obiektu i bibliotek.  
  
 Aby rozwiązać C1047, Odbuduj wszystkich plików obiektu i bibliotek.