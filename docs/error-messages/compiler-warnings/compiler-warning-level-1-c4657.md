---
title: Ostrzeżenie kompilatora (poziom 1) C4657
ms.date: 11/04/2016
f1_keywords:
- C4657
helpviewer_keywords:
- C4657
ms.assetid: eb750050-cea6-4ead-b80c-d5dcd4971cfc
ms.openlocfilehash: 6cc049d99339a6f19ca86cd5c7a10f062a1451a9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199503"
---
# <a name="compiler-warning-level-1-c4657"></a>Ostrzeżenie kompilatora (poziom 1) C4657

wyrażenie zawiera typ danych, który jest nowy od czasu ostatniej kompilacji

Dodano lub Zmieniono typ danych, co sprawia, że nowy kod źródłowy od momentu ostatniej pomyślnej kompilacji. Edytuj i Kontynuuj nie obsługuje zmian istniejących typów danych.

To ostrzeżenie będzie zawsze następuje po [błędzie krytycznym C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu](/visualstudio/debugger/supported-code-changes-cpp).

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Aby usunąć to ostrzeżenie bez kończenia bieżącej sesji debugowania

1. Przed błędem Zmień typ danych z powrotem na stan.

1. Z menu **Debuguj** wybierz polecenie **Zastosuj zmiany kodu**.

### <a name="to-remove-this-error-without-changing-your-source-code"></a>Aby usunąć ten błąd bez zmiany kodu źródłowego

1. Z menu **Debuguj** wybierz polecenie **Zatrzymaj debugowanie**.

1. Z menu **kompilacja** wybierz polecenie **Kompiluj**.
