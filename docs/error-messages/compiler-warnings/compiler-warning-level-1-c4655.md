---
title: Ostrzeżenie kompilatora (poziom 1) C4655
ms.date: 08/27/2018
f1_keywords:
- C4655
helpviewer_keywords:
- C4655
ms.assetid: 540f2c7a-e4a1-49af-84b4-03eeea1bbf41
ms.openlocfilehash: d4c409c2d69099853a872142e05ef0fcda5a7655
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199534"
---
# <a name="compiler-warning-level-1-c4655"></a>Ostrzeżenie kompilatora (poziom 1) C4655

> "*symbol*": typ zmiennej jest nowy od czasu ostatniej kompilacji lub został inaczej zdefiniowany w innym miejscu

## <a name="remarks"></a>Uwagi

Został zmieniony lub dodany nowy typ danych od czasu ostatniej pomyślnej kompilacji. Edytuj i Kontynuuj nie obsługuje zmian istniejących typów danych.

To ostrzeżenie następuje po [błędzie krytycznym C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu](/visualstudio/debugger/supported-code-changes-cpp).

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Aby usunąć to ostrzeżenie bez kończenia bieżącej sesji debugowania

1. Przed błędem Zmień typ danych z powrotem na stan.

2. Z menu **Debuguj** wybierz polecenie **Zastosuj zmiany kodu**.

### <a name="to-remove-this-warning-without-changing-your-source-code"></a>Aby usunąć to ostrzeżenie bez zmiany kodu źródłowego

1. Z menu **Debuguj** wybierz polecenie **Zatrzymaj debugowanie**.

2. Z menu **kompilacja** wybierz polecenie **Kompiluj**.
