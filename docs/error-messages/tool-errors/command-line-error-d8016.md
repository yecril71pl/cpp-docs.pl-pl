---
title: Błąd d8016 wiersza polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8016
dev_langs:
- C++
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ee16542b2f0cf9842e351813ed2e0b0d22cccaa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056992"
---
# <a name="command-line-error-d8016"></a>Błąd D8016 wiersza polecenia

Opcje wiersza polecenia "opcja1" i "opcja2" są niezgodne

Nie można jednocześnie określić opcji wiersza polecenia.

Sprawdź zmienne środowiskowe, takie jak CL, dla opcji specyfikacji.

**/ CLR** oznacza **/eha**, i nie można określić inne **/EH** — opcja kompilatora przy użyciu **/CLR**. Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).

D8016 może wystąpić po uaktualnieniu projektu Visual C++ 6.0: proces Kreatora aktualizacji projektu mogą umożliwiać **usunęliśmy** dla każdego pliku kodu źródłowego w projekcie, który zastępuje **usunęliśmy** ustawienie dla projektu.  Aby rozwiązać problem, zmień **usunęliśmy** ustawień dla każdego pliku kodu źródłowego w projekcie ustawienie domyślne, co oznacza, że ustawienia projektu dla **usunęliśmy** będą obowiązywać dla każdego pliku.

Zobacz [usunęliśmy (kontrole błąd czasu wykonywania)](../../build/reference/rtc-run-time-error-checks.md) informacji na temat zmiany **usunęliśmy** ustawienie właściwości.