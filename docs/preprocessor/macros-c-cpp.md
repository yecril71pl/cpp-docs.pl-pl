---
title: Makra (C/C++)
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessor
- preprocessor, macros
- Visual C++, preprocessor macros
ms.assetid: a7bfc5d4-2537-4fe0-bef0-70cec0b43388
ms.openlocfilehash: 281aaf686c07894b5cb1fab187ba903179c51de8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371781"
---
# <a name="macros-cc"></a>Makra (C/C++)
Wstępne przetwarzanie rozszerza makra we wszystkich wierszach, które nie są dyrektywami preprocesora (wiersze, które nie mają **#** jako pierwszy znak inny niż biały) w części niektórych dyrektyw, które nie są pomijane jako część kompilacja warunkowa. Dyrektywy „kompilacji warunkowej” pozwalają na pomijanie kompilacji części pliku źródłowego przez testowanie wyrażenia stałego lub identyfikatora służącego do określania bloków tekstu, które są przekazywane do kompilatora i bloków tekstu, które są usuwane z pliku źródłowego podczas przetwarzania wstępnego.

Dyrektywa `#define` jest zazwyczaj używana do kojarzenia znaczących identyfikatorów ze stałymi, słowami kluczowymi i powszechnie używanymi instrukcjami lub wyrażeniami. Identyfikatory, które reprezentują stałe są czasami nazywane „stałymi symbolicznymi” lub „stałymi manifestu”. Identyfikatory, które reprezentują instrukcje lub wyrażenia są nazywane „makrami”. W tej dokumentacji preprocesora, używany jest jedynie termin „makro”.

Po rozpoznaniu nazwy makra w tekście źródłowym programu lub w argumentach niektórych poleceń preprocesora, jest ona traktowana jako wywołanie tego makra. Nazwa makra jest zamieniana przez kopię ciała makra. Jeśli makro akceptuje argumenty, rzeczywiste argumenty następujące po nazwie makra są zastępowane parametrami formalnymi w ciele makra. Proces zamiany wywołania makra przetworzoną kopią ciała nazywa się „rozszerzeniem” wywołania makra.

W praktyce, istnieją dwa typy makr. „Obiektopodobne” makra nie przyjmują żadnych argumentów, tymczasem „funkcjopodobne” makra można zdefiniować aby przyjmowały argumenty oraz aby wyglądały i zachowywały się jak wywołania funkcji. Ponieważ makra nie generują rzeczywistych wywołań funkcji, można czasami przyspieszyć działanie programów zamieniając wywołania funkcji na makra. (W języku C++, funkcje wbudowane są często metodą preferowaną). Jednakże makra mogą tworzyć problemy, jeśli nie będą zdefiniowane i używane ostrożnie. Może zaistnieć potrzeba użycia nawiasów w definicji makra z argumentami, aby zachować właściwą kolejność w wyrażeniu. Ponadto, makra mogą nie obsługiwać poprawnie wyrażeń z efektami ubocznymi. Zobacz `getrandom` przykładu w [#define — dyrektywa](../preprocessor/hash-define-directive-c-cpp.md) Aby uzyskać więcej informacji.

Po zdefiniowaniu makra nie można przedefiniować go na inną wartość, bez usuwania oryginalnej definicji. Jednakże, można ponownie zdefiniować makro z identyczną definicją. W efekcie ta sama definicja może pojawić się w programie więcej niż jeden raz.

`#undef` Dyrektywy usuwa definicję makra. Po usunięciu definicji, można ponownie zdefiniować makro z inną wartością. [#Define — dyrektywa](../preprocessor/hash-define-directive-c-cpp.md) i [dyrektywa #undef](../preprocessor/hash-undef-directive-c-cpp.md) omówić `#define` i `#undef` dyrektyw, odpowiednio.

Aby uzyskać więcej informacji, zobacz,

- [Makra i język C++](../preprocessor/macros-and-cpp.md)

- [Makra wariadyczne](../preprocessor/variadic-macros.md)

- [Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)

## <a name="see-also"></a>Zobacz także

[Dokumentacja preprocesora języka C/C++](../preprocessor/c-cpp-preprocessor-reference.md)