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
ms.openlocfilehash: ccd36c5edaaab8577e5f278b25b51ce69e0633f1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile (interpretacja słowa kluczowego volatile)

Określa sposób [volatile](../../cpp/volatile-cpp.md) — słowo kluczowe jest interpretowane.

## <a name="syntax"></a>Składnia

> **/ volatile:**{**iso**|**ms**}  

## <a name="arguments"></a>Argumenty

**/volatile:iso**  
Wybiera strict `volatile` semantyki zgodnie z definicją w języku C++ normy ISO. Uzyskaj/Wydaj semantykę nie ma gwarancji w dostępie nietrwałym. Czy kompilator jest przeznaczony dla ARM, jest on domyślnej interpretacji `volatile`.

**/volatile:MS**  
Wybiera rozszerzone firmy Microsoft `volatile` semantyki, który dodać pamięci porządkowanie gwarancje poza języka C++ normy ISO. Uzyskaj/Wydaj semantykę są gwarantowaną w dostępie nietrwałym. Ta opcja wymusza także kompilatorowi Generowanie bariery pamięci sprzętu, które może dodać znaczne obciążenie ARM i innych słabe architektur porządkowania pamięci. Czy kompilator jest przeznaczony dla dowolnej platformy, z wyjątkiem ARM, jest on domyślnej interpretacji `volatile`.

## <a name="remarks"></a>Uwagi

Zdecydowanie zaleca się używanie **/volatile:iso** oraz jawna synchronizacja elementów podstawowych i funkcje wewnętrzne kompilatora, gdy mamy do czynienia pamięci, który jest współużytkowany przez wątki. Aby uzyskać więcej informacji, zobacz [volatile](../../cpp/volatile-cpp.md).

Jeśli port istniejący kod lub zmienić tej opcji w trakcie projektu, może być przydatne umożliwienie ostrzeżenie [C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md) do identyfikowania lokalizacji kodu, których dotyczy różnica semantyki.

Brak nie `#pragma` odpowiednikiem kontroli tej opcji.

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>Aby ustawić / volatile — opcja kompilatora w programie Visual Studio

1. Otwórz **strony właściwości** okno dialogowe dla projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** strony właściwości.

1. W **dodatkowe opcje** Dodaj **/volatile:iso** lub **/volatile:ms** , a następnie wybierz **OK** lub **Zastosuj** Aby zapisać zmiany.

## <a name="see-also"></a>Zobacz także

[volatile](../../cpp/volatile-cpp.md)  
[Opcje kompilatora](../../build/reference/compiler-options.md)  
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)  
