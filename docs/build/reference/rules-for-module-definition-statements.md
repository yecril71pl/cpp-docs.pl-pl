---
title: "Zasady dla instrukcji definicji modułu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .def
dev_langs: C++
helpviewer_keywords:
- module definition files, statement syntax
- module definition files
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 40eb4875b195871aff8d274667e005d63424a110
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="rules-for-module-definition-statements"></a>Zasady dla instrukcji definicji modułu
Wszystkie instrukcje w pliku .def mają zastosowanie następujące reguły składni. Inne zasady, które są stosowane do instrukcji określonych opisano z każdej instrukcji.  
  
-   Instrukcje, atrybut słów kluczowych i identyfikatory określone przez użytkownika jest wielkość liter.  
  
-   Długie nazwy zawierające spacje lub średnikami (;) plików musi być ujęta w znaki cudzysłowu (").  
  
-   Aby rozdzielić słowo kluczowe instrukcji z jego argumentów i aby oddzielić od siebie — instrukcje, należy użyć co najmniej jeden spacje, tabulatory lub znakami nowego wiersza. Dwukropkiem (:) lub znak równości (=), który wyznacza argument będzie otoczona zero lub więcej spacje, tabulatory lub znakami nowego wiersza.  
  
-   A **nazwa** lub **biblioteki** instrukcji, jeśli używany, musi poprzedzać wszystkie inne instrukcje.  
  
-   **Sekcje** i **EKSPORTÓW** instrukcje może występować więcej niż raz w pliku .def. Każda instrukcja może zająć wiele specyfikacji, które muszą być oddzielone co najmniej jeden spacje, tabulatory lub znakami nowego wiersza. Instrukcja — słowo kluczowe musi występować po przed pierwszym specyfikacji i można powtarzać przed każdy dodatkowego specyfikacji.  
  
-   Wiele instrukcji ma równoważnej łącze opcji wiersza polecenia. Zobacz opis odpowiedniej opcji łącze, aby uzyskać dodatkowe szczegóły.  
  
-   Komentarze w pliku .def są oznaczane średnikiem (;) na początku każdego wiersza komentarza. Komentarz nie mogą współużytkować wiersz z instrukcją, ale może być wyświetlany między specyfikacjami w wielowierszowym instrukcji. (**Sekcje** i **EKSPORTÓW** są instrukcje wielowierszowy.)  
  
-   Liczbowa argumenty są określone w podstawie 10 lub szesnastkową.  
  
-   Jeśli argument ciągu odpowiada [słowa zarezerwowanego](../../build/reference/reserved-words.md), musi być ujęta w znaki cudzysłowu (").  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki definicji modułu (.Def)](../../build/reference/module-definition-dot-def-files.md)  