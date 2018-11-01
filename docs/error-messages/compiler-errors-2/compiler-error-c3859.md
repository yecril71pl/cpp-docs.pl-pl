---
title: Błąd kompilatora C3859
ms.date: 11/04/2016
f1_keywords:
- C3859
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
ms.openlocfilehash: be6ccaab49cb329e862fb6068af1337eddbaac8f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490284"
---
# <a name="compiler-error-c3859"></a>Błąd kompilatora C3859

zakres pamięci wirtualnej dla PCH przekroczona; należy ponownie skompilować przy użyciu opcji wiersza polecenia "-Zmvalue" lub nowszej

Twoje prekompilowany plik nagłówkowy jest zbyt małe ilości danych, którą kompilator próbuje umieścić w niej. Użyj **/Zm** flagi kompilatora, aby określić większa wartość dla prekompilowanego pliku nagłówkowego. Aby uzyskać więcej informacji, zobacz [/Zm (Określ wstępnie skompilowany nagłówek Memory Allocation Limit)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).