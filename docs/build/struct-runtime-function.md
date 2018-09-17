---
title: Struktura RUNTIME_FUNCTION | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 84386527-d3aa-41c5-871d-78e3e1913704
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f3831dc36664c556cf0a020ed87c60200443fd3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718240"
---
# <a name="struct-runtimefunction"></a>struktura RUNTIME_FUNCTION

Obsługa wyjątków na podstawie tabeli wymaga wpisu tabeli dla wszystkich funkcji, które alokacji stosu lub wywołać inną funkcję (na przykład funkcje niebędącym elementem typu liść). Funkcja wpisów tabeli mają format:

|||
|-|-|
|ULONG|Adres początkowy — funkcja|
|ULONG|Adres końcowy — funkcja|
|ULONG|Operacja unwind info adresu|

Struktura RUNTIME_FUNCTION muszą być wyrównane w pamięci typu DWORD. Wszystkie adresy są względne obrazu, oznacza to, że są one 32-bitowe przesunięcia od adres początkowy obrazu, który zawiera wpis tabeli funkcji. Te wpisy są sortowane i umieścić w sekcji .pdata obrazu je typu PE32 +. Dla funkcji dynamicznie generowanym [JIT kompilatory] środowisko uruchomieniowe do obsługi tych funkcji, należy użyć RtlInstallFunctionTableCallback lub RtlAddFunctionTable może przekazać tę informację do systemu operacyjnego. Niewykonanie tej czynności spowoduje zawodnych wyjątków, obsługa i debugowanie procesów.

## <a name="see-also"></a>Zobacz też

[Dane operacji Unwind dla obsługi wyjątków, obsługa debugera](../build/unwind-data-for-exception-handling-debugger-support.md)