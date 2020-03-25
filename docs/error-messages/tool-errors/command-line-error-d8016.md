---
title: Błąd D8016 wiersza polecenia
ms.date: 11/04/2016
f1_keywords:
- D8016
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
ms.openlocfilehash: 1bdef16b14488be86aff880db7c049f4bcddcdb5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196966"
---
# <a name="command-line-error-d8016"></a>Błąd D8016 wiersza polecenia

Opcje wiersza polecenia "opcja1" i "opcja2" są niezgodne

Nie można jednocześnie określić opcji wiersza polecenia.

Sprawdź zmienne środowiskowe, takie jak CL, dla specyfikacji opcji.

**/CLR** oznacza **/EHa**i nie można określić żadnej innej opcji kompilatora **/EH** z **/CLR**. Aby uzyskać więcej informacji, zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md).

Po aktualizacji projektu programu Visual C++ 6,0 można uzyskać D8016 wiersza polecenia: proces kreatora aktualizacji projektu może włączyć **/RTC** dla każdego pliku kodu źródłowego w projekcie, który zastępuje ustawienie **/RTC** dla projektu.  Aby rozwiązać ten problem, Zmień ustawienie **/RTC** dla każdego pliku kodu źródłowego w projekcie na ustawienie domyślne, co oznacza, że ustawienie projektu dla **/RTC** będzie obowiązywać dla każdego pliku.

Zobacz [/RTC (sprawdzanie błędów czasu wykonywania)](../../build/reference/rtc-run-time-error-checks.md) , aby uzyskać informacje na temat zmiany ustawienia właściwości **/RTC** .
