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
ms.openlocfilehash: d6f9709da189403f2594d76751430d30554bffe5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300621"
---
# <a name="command-line-error-d8016"></a>Błąd D8016 wiersza polecenia
Opcja "1" i "option2" Opcje wiersza polecenia są niezgodne  
  
 Nie można jednocześnie określić opcje wiersza polecenia.  
  
 Sprawdź zmienne środowiskowe, takie jak CL, dla opcji specyfikacji.  
  
 **/ CLR** oznacza **/eha**, i nie można określić innych **/EH** — opcja kompilatora z **/CLR**. Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 Mogą wystąpić d8016 polecenia po zaktualizowaniu [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 6.0 projektu: procesu Kreatora aktualizacji projektu mogą umożliwić **/RTC** dla każdego pliku kodu źródłowego w projekcie, który zastępuje **/RTC** ustawienie Projekt.  Aby rozwiązać, zmień **/RTC** ustawienie dla każdego pliku kodu źródłowego w projekcie do domyślnych ustawień, co oznacza, że ustawienie projektu **/RTC** będzie obowiązywać dla każdego pliku.  
  
 Zobacz [/RTC (błąd czasu wykonywania sprawdza)](../../build/reference/rtc-run-time-error-checks.md) informacji na temat zmiany **/RTC** ustawienie właściwości.