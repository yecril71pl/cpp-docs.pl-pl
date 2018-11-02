---
title: struktura RUNTIME_FUNCTION
ms.date: 11/04/2016
ms.assetid: 84386527-d3aa-41c5-871d-78e3e1913704
ms.openlocfilehash: 6b113f6cf1e9951f9e4578e15c9ed0af3d036fa6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520253"
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