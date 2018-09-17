---
title: -volatile (interpretacja słowa kluczowego volatile) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /volatile:iso
- /volatile:ms
- /volatile
dev_langs:
- C++
helpviewer_keywords:
- /volatile compiler option
- /volatile compiler option [C++]
- -volatile compiler option
- volatile compiler option [C++]
- volatile compiler option
- -volatile compiler option [C++]
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4204d602d1390bf30080a800174426513faf0467
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723637"
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile (interpretacja słowa kluczowego volatile)

Określa sposób, w jaki [volatile](../../cpp/volatile-cpp.md) — słowo kluczowe, które ma być interpretowany.

## <a name="syntax"></a>Składnia

> **/ volatile:**{**iso**|**ms**}

## <a name="arguments"></a>Argumenty

**/volatile:iso**<br/>
Wybiera ścisłą `volatile` semantyki zgodnie z definicją języka ISO standard C++. Semantyka nabycia/wydania nie jest gwarantowana przy dostępach lotnych. Jeśli kompilator jest przeznaczony dla ARM, jest to domyślna interpretacja `volatile`.

**/volatile:MS**<br/>
Wybiera rozszerzone firmy Microsoft `volatile` semantykę, która Dodaj gwarancje pamięci zamawiania ponad ISO standard C++ — język. Semantyka nabycia/wydania jest gwarantowana przy dostępach lotnych. Tej opcji zmusza również kompilator do generowania sprzętowych barier pamięci, które może dodać znaczne obciążenie na ARM i innych słabych architektur zamawiających pamięć. Jeśli kompilator jest przeznaczony dla dowolnej platformy, z wyjątkiem ARM, jest to domyślna interpretacja `volatile`.

## <a name="remarks"></a>Uwagi

Zdecydowanie zalecamy użycie **/volatile:iso** wraz z jawnymi podstawami synchronizacji i niejawnymi, gdy masz do czynienia z pamięcią, która jest udostępniona w wielu wątkach. Aby uzyskać więcej informacji, zobacz [volatile](../../cpp/volatile-cpp.md).

Jeśli przeniesiesz istniejący kod lub zmień opcję w środku projektu, może być pomocne włączenie ostrzeżenia [C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md) do identyfikowania lokalizacji kodu, których dotyczy różnice w semantyce.

Istnieje nie `#pragma` równoważne do kontrolowania tej opcji.

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>Aby ustawić / volatile — opcja kompilatora w programie Visual Studio

1. Otwórz **stron właściwości** okno dialogowe dla projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. W **dodatkowe opcje** Dodaj **/volatile:iso** lub **/volatile:ms** , a następnie wybierz **OK** lub **Zastosuj** Aby zapisać zmiany.

## <a name="see-also"></a>Zobacz także

[volatile](../../cpp/volatile-cpp.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)
