---
title: Kompilator ostrzeżenie (poziom 1) C4819
ms.date: 11/04/2016
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: c0ca29a304fbd05cb0c6b7d1b06414304c70fb2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596615"
---
# <a name="compiler-warning-level-1-c4819"></a>Kompilator ostrzeżenie (poziom 1) C4819

Plik zawiera znak, który nie może być przedstawiony w bieżącej stronie kodowej (liczba). Zapisz plik w formacie Unicode, aby zapobiec utracie danych.

C4819 występuje, gdy plik źródłowy ANSI jest skompilowany w systemie ze stroną kodową, która nie może reprezentować wszystkie znaki w pliku.

Aby rozwiązać C4819, Zapisz plik w formacie Unicode. W programie Visual Studio, wybierz **pliku**, **zaawansowane opcje zapisywania**. W **zaawansowane opcje zapisywania** okna dialogowego Wybierz kodowanie, które może reprezentować wszystkie znaki w pliku — na przykład, UTF-8 — a następnie wybierz **OK**.