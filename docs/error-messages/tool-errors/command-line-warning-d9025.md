---
title: Ostrzeżenie D9025 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9025
dev_langs:
- C++
helpviewer_keywords:
- D9025
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3875a2cbd065fd5ad887267bcc80748fa9845d0d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="command-line-warning-d9025"></a>Ostrzeżenie D9025 dla wiersza polecenia
zastępowanie opcja ' 1' z "option2"  
  
 *Opcja 1* opcji została określona, ale następnie została zastąpiona przez *option2*. *Option2* użyto opcji.  
  
 Jeśli dwie opcje określić dyrektywy sprzeczne lub niezgodne, używana jest dyrektywy określona lub implikowana w opcji najdalej z prawej w wierszu polecenia.  
  
 Jeśli uzyskać to ostrzeżenie w przypadku kompilowania kodu ze środowiska projektowego i nie ma pewności, których pochodzą z opcje powodujące konflikt, należy rozważyć następujące kwestie:  
  
-   Opcję można określić w kodzie lub w ustawieniach projektu z projektu. Jeśli przyjrzymy się przez kompilator [strony właściwości wiersza polecenia](../../ide/command-line-property-pages.md) i jeśli wyświetlane opcje powodujące konflikt w **wszystkie opcje** pola, a następnie opcje są ustawione na stronach właściwości projektu, w przeciwnym razie wartość opcji są ustawiane w kodzie źródłowym.  
  
     Jeśli opcje są ustawione na stronach właściwości projektu, sprawdź na stronie właściwości preprocesora kompilatora (z węzła projektu wybraną w Eksploratorze rozwiązań).  Jeśli użytkownik nie widzi opcji tam ustawione, należy sprawdzić ustawienia strony właściwości preprocesora dla każdego pliku kodu źródłowego (w Eksploratorze rozwiązań) upewnij się, że nie został dodany istnieje.  
  
     Jeśli opcje są ustawione w kodzie można ustawić w kodzie lub w nagłówkach systemu windows.  Możesz spróbować tworzenia wstępnie przetworzonych plików ([/P](../../build/reference/p-preprocess-to-a-file.md)) i wyszukaj symbolu.