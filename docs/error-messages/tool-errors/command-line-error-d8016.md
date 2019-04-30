---
title: Błąd D8016 wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D8016
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
ms.openlocfilehash: c1e2e3e28f8556416f58d68f8ef1df4b220bc54c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399970"
---
# <a name="command-line-error-d8016"></a>Błąd D8016 wiersza polecenia

Opcje wiersza polecenia "opcja1" i "opcja2" są niezgodne

Nie można jednocześnie określić opcji wiersza polecenia.

Sprawdź zmienne środowiskowe, takie jak CL, dla opcji specyfikacji.

**/ CLR** oznacza **/eha**, i nie można określić inne **/EH** — opcja kompilatora przy użyciu **/CLR**. Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).

D8016 może wystąpić po uaktualnieniu projektu Visual C++ 6.0: proces Kreatora aktualizacji projektu mogą umożliwiać **usunęliśmy** dla każdego pliku kodu źródłowego w projekcie, który zastępuje **usunęliśmy** ustawienie dla projektu.  Aby rozwiązać problem, zmień **usunęliśmy** ustawień dla każdego pliku kodu źródłowego w projekcie ustawienie domyślne, co oznacza, że ustawienia projektu dla **usunęliśmy** będą obowiązywać dla każdego pliku.

Zobacz [usunęliśmy (kontrole błąd czasu wykonywania)](../../build/reference/rtc-run-time-error-checks.md) informacji na temat zmiany **usunęliśmy** ustawienie właściwości.