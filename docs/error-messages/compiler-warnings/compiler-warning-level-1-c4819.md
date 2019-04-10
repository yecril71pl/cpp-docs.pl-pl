---
title: Kompilator ostrzeżenie (poziom 1) C4819
ms.date: 04/08/2019
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: d43b49d473e7113d8cdfb89aaa6e93045e13d0f7
ms.sourcegitcommit: 39debf8c525c3951af6913ee5e514617658f8859
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59424225"
---
# <a name="compiler-warning-level-1-c4819"></a>Kompilator ostrzeżenie (poziom 1) C4819

> Plik zawiera znak, który nie może być przedstawiony w bieżącej stronie kodowej (*numer*). Zapisz plik w formacie Unicode, aby zapobiec utracie danych.

C4819 występuje podczas kompilowania pliku źródłowego ANSI w systemie przy użyciu strony kodowej, który nie może reprezentować wszystkie znaki w pliku.

Istnieje kilka sposobów, aby rozwiązać C4819. Prostym sposobem jest usunięcie wskazuje niedozwolony znak, jeśli nie potrzebujesz go, na przykład, jeśli znajduje się w komentarzu. Systemowa strona kodowa można ustawić w Panelu sterowania, które obsługuje zestaw znaków wykorzystywany przez kod źródłowy. Unicode można użyć [sekwencje unikowe](/cpp/c-language/escape-sequences) Aby utworzyć znaki lub ciągi, korzystających z podstawowych ANSI znak zestawu w kodzie źródłowym. Na koniec można zapisać pliku w formacie Unicode, za pomocą podpisu, znany także jako znacznik kolejności bajtów (BOM).

Aby zapisać plik w formacie Unicode, w programie Visual Studio, wybierz opcję **pliku** > **Zapisz jako**. W **Zapisz plik jako** okna dialogowego Wybierz listę rozwijaną na **Zapisz** przycisk, a następnie wybierz **Zapisz z kodowaniem**. Jeśli zapiszesz tę samą nazwę pliku, może być konieczne upewnij się, że chcesz zastąpić ten plik. W **zaawansowane opcje zapisywania** okno dialogowe, wybierz kodowanie, który może reprezentować wszystkie znaki w pliku — na przykład **Unicode (UTF-8 z podpisem) - strona kodowa 65001**— a następnie wybierz  **OK**.