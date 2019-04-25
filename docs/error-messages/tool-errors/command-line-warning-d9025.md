---
title: Ostrzeżenie D9025 dla wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D9025
helpviewer_keywords:
- D9025
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
ms.openlocfilehash: e7090dda72868ad7ee4d5f8e4f1ba6a0ad121c98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214124"
---
# <a name="command-line-warning-d9025"></a>Ostrzeżenie D9025 dla wiersza polecenia

zastępowanie opcja "1" z "opcja2"

*Opcja1* opcji została określona, ale następnie została zastąpiona przez *opcja2*. *Opcja2* użyto opcji.

Dwie opcje określenia sprzecznych lub niezgodne dyrektywy, zostanie użyta dyrektywy określone lub też dorozumianych, w przypadku opcji najdalej z prawej strony w wierszu polecenia.

Jeśli pobieranie tego ostrzeżenia podczas kompilowania środowiska programowania, a nie pewności, skąd pochodzą opcje powodujące konflikt, należy rozważyć następujące kwestie:

- Opcjonalnie można określić w kodzie lub w ustawieniach projektu z projektu. Jeśli przyjrzymy się kompilatora [strony właściwości wiersza polecenia](../../build/reference/command-line-property-pages.md) i jeśli widzisz opcje powodujące konflikt w **wszystkie opcje** pola, a następnie opcje są ustawione na stronach właściwości projektu, w przeciwnym razie, opcje są ustawione w kodzie źródłowym.

   Jeśli opcje są ustawione na stronach właściwości projektu, sprawdź na stronie właściwości preprocesora kompilatora (z węzła projektu wybranego w oknie Solution Explorer).  Jeśli nie widzisz opcji tam ustawione, sprawdź ustawienia strony preprocesora właściwości dla każdego pliku kodu źródłowego (w Eksploratorze rozwiązań), aby upewnić się, nie został dodany istnieje.

   Jeśli opcje są ustawione w kodzie można ustawić w kodzie lub w nagłówkach systemu windows.  Możesz spróbować tworzenia wstępnie przetworzonego pliku ([/P](../../build/reference/p-preprocess-to-a-file.md)) i wyszukaj symbolu.