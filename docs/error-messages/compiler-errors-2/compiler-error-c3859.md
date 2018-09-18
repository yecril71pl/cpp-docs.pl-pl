---
title: Błąd kompilatora C3859 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3859
dev_langs:
- C++
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ac06a09a6ad66384fd2b5423e3df046771f7653
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053392"
---
# <a name="compiler-error-c3859"></a>Błąd kompilatora C3859

zakres pamięci wirtualnej dla PCH przekroczona; należy ponownie skompilować przy użyciu opcji wiersza polecenia "-Zmvalue" lub nowszej

Twoje prekompilowany plik nagłówkowy jest zbyt małe ilości danych, którą kompilator próbuje umieścić w niej. Użyj **/Zm** flagi kompilatora, aby określić większa wartość dla prekompilowanego pliku nagłówkowego. Aby uzyskać więcej informacji, zobacz [/Zm (Określ wstępnie skompilowany nagłówek Memory Allocation Limit)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).