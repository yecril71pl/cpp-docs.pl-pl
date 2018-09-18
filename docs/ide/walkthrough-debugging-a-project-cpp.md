---
title: 'Wskazówki: Debugowanie projektu (C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 09/14/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- projects [C++], debugging
- project debugging [C++]
- debugging projects
ms.assetid: a5cade77-ba51-4b03-a7a0-6897e3cd6a59
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 914eb26384a32c9a81a153db04c10708eb42e652
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056538"
---
# <a name="walkthrough-debugging-a-project-c"></a>Wskazówki: debugowanie projektu (C++)
W tym przewodniku możesz zmodyfikować program, aby rozwiązać ten problem, które wykryte podczas testowania projektu.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
- W tym przewodniku przyjęto założenie, że rozumiesz podstawy języka C++.  
  
- Przyjęto również założenie, że zostały wykonane wcześniej pokrewne instruktaże, które są wymienione w [przy użyciu programu Visual Studio IDE dla programowanie aplikacji klasycznych w języku C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
### <a name="to-fix-a-program-that-has-a-bug"></a>Aby naprawić program, który zawiera usterkę  
  
1. Aby zobaczyć, co występuje, gdy `Cardgame` obiekt jest niszczony, wyświetlanie destruktor dla `Cardgame` klasy.  
  
     Na pasku menu wybierz **widoku** > **Widok klas**.  
  
     W **Widok klas** okna, rozwiń węzeł **gry** drzewa projektu i wybierz pozycję **wartość Cardgame** klasy, aby wyświetlić elementy członkowskie klasy i metody.  
  
     Otwórz menu skrótów dla **~Cardgame(void)** destruktora, a następnie wybierz **przejdź do definicji**.  
  
1. Aby zmniejszyć `totalParticipants` po karcianej, Dodaj następujący kod między otwierające i zamykające nawiasy klamrowe z `Cardgame::~Cardgame` destruktora.  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#110](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_1.cpp)]  
  
1. Plik Cardgame.cpp powinny przypominać po zmianach przypominać:  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#111](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_2.cpp)]  
  
1. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.  
  
1. Po zakończeniu kompilacji, uruchom go w trybie debugowania, wybierając **debugowania** > **Rozpocznij debugowanie** na pasku menu lub wybierając **F5** klucza. Program wstrzymuje w pierwszym punkcie przerwania.  
  
1. Aby przejść przez program, na pasku menu wybierz **debugowania** > **Step Over**, lub wybierz **F10** klucza.  
  
     Należy zauważyć, że po każdym poleceniu `Cardgame` Konstruktor wykonuje wartość `totalParticipants` zwiększa się. Gdy `PlayGames` funkcja zwróci wartość, ponieważ do każdego `Cardgame` wystąpienie wykracza poza zakres i zostanie usunięta i destruktor jest wywoływany, `totalParticipants` zmniejsza. Tuż przed `return` instrukcja jest wykonywana, `totalParticipants` jest równa 0.  
  
1. Kontynuuj przechodzenie krok po kroku za pośrednictwem programu aż do jej zakończenia lub pozwolić mu działać, wybierając **debugowania** > **Uruchom** na pasku menu lub wybierając **F5** klucza.  
  
## <a name="next-steps"></a>Następne kroki  

**Poprzedni:** [wskazówki: Testowanie projektu (C++)](../ide/walkthrough-testing-a-project-cpp.md)<br/> 
**Następnie:** [wskazówki: Wdrażanie Twojego programu (C++)](../ide/walkthrough-deploying-your-program-cpp.md)<br/>
  
## <a name="see-also"></a>Zobacz też  

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)<br/>
