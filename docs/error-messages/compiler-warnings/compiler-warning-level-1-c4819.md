---
title: Ostrzeżenie kompilatora (poziom 1) C4819
ms.date: 04/08/2019
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: f81a4f44a489e2e4c5bd5c063d922129581819f9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509370"
---
# <a name="compiler-warning-level-1-c4819"></a>Ostrzeżenie kompilatora (poziom 1) C4819

> Plik zawiera znak, który nie może być przedstawiony w bieżącej stronie kodowej (*Number*). Zapisz plik w formacie Unicode, aby zapobiec utracie danych.

C4819 występuje podczas kompilowania pliku źródłowego ANSI w systemie przy użyciu strony kodowej, która nie może reprezentować wszystkich znaków w pliku.

Istnieje kilka sposobów na rozwiązanie C4819. Jeden prosty sposób polega na usunięciu znaku powodującego problemy, jeśli nie jest on potrzebny, na przykład jeśli jest w komentarzu. Można ustawić stronę kodową systemu w panelu sterowania na taką, która obsługuje zestaw znaków używany przez kod źródłowy. [Sekwencje unikowe](../../c-language/escape-sequences.md) Unicode mogą służyć do tworzenia znaków lub ciągów, które używają tylko podstawowego znaku ANSI w kodzie źródłowym. Na koniec można zapisać plik w formacie Unicode za pomocą podpisu, znanego również jako znacznik kolejności bajtów (BOM).

Aby zapisać plik w formacie Unicode, w programie Visual Studio wybierz pozycję **plik**  >  **Zapisz jako**. W oknie dialogowym **Zapisz plik jako** wybierz listę rozwijaną na przycisku **Zapisz** , a następnie wybierz pozycję **Zapisz z kodowaniem**. Jeśli zapiszesz w tej samej nazwie pliku, może być konieczne potwierdzenie, że chcesz zastąpić plik. W oknie dialogowym **Zaawansowane opcje zapisywania** wybierz kodowanie, które może reprezentować wszystkie znaki w pliku — na przykład **Unicode (UTF-8 z podpisem)-strona kodowa 65001**, a następnie wybierz **przycisk OK**.
