---
title: Struktura RUNTIME_FUNCTION | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 84386527-d3aa-41c5-871d-78e3e1913704
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c05dcd516af5c078b4e4e664bae16f65370ca117
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="struct-runtimefunction"></a>struktura RUNTIME_FUNCTION
Obsługa wyjątków na podstawie tabeli wymaga wpisu tabeli dla wszystkich funkcji, które przydzielenie miejsca na stosie lub wywołać funkcję innego (na przykład funkcje niebędącym elementem typu liść). Funkcja wpisów tabeli mają format:  
  
|||  
|-|-|  
|ULONG|Adres początkowy — funkcja|  
|ULONG|Adres końcowy — funkcja|  
|ULONG|Informacje o adres unwind|  
  
 Struktura RUNTIME_FUNCTION musi być typu DWORD wyrównane w pamięci. Wszystkie adresy są obrazu względną, oznacza to, że są one 32-bitowe przesunięcia od adres początkowy obrazu, który zawiera wpisu tabeli funkcji. Te wpisy są sortowane i umieścić w sekcji .pdata obrazu plikiem PE32 +. Dynamicznie generowanym funkcji [kompilatory JIT] środowiska uruchomieniowego do obsługi tych funkcji należy użyć RtlInstallFunctionTableCallback lub RtlAddFunctionTable może przekazać tę informację do systemu operacyjnego. Błąd w tym celu spowoduje zawodnych wyjątków, obsługa i debugowanie procesów.  
  
## <a name="see-also"></a>Zobacz też  
 [Dane operacji Unwind dla obsługi wyjątków, obsługa debugera](../build/unwind-data-for-exception-handling-debugger-support.md)