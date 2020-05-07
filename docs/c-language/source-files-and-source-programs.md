---
title: Pliki źródłowe i programy źródłowe
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++], source
- programs [C++], source
- source files, specifying in compiler
- source programs
ms.assetid: 18bb2826-17da-48e5-92a2-10e649f1bc9f
ms.openlocfilehash: ac906925be551c6ee4da08e200d4028047b3d041
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349885"
---
# <a name="source-files-and-source-programs"></a>Pliki źródłowe i programy źródłowe

Program źródłowy można podzielić na jeden lub więcej „plików źródłowych” lub „jednostek translacji”. Dane wejściowe kompilatora nazywane są „jednostką translacji”.

## <a name="syntax"></a>Składnia

*Jednostka translation*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracja zewnętrzna* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracja zewnętrzna* *jednostki tłumaczenia*

*deklaracja zewnętrzna*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Definicja funkcji*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*oświadczeń*

[Przegląd deklaracji](../c-language/overview-of-declarations.md) zawiera składnię dla `declaration` Nieterminalu, a *Dokumentacja preprocesora* wyjaśnia, jak jest przetwarzana [Jednostka tłumaczenia](../preprocessor/phases-of-translation.md) .

> [!NOTE]
> Zapoznaj się z artykułem wprowadzenie do [podsumowania składni języka C](../c-language/c-language-syntax-summary.md), aby zapoznać się z opisem Konwencji składni ANSI.

Składniki jednostki translacji są deklaracjami zewnętrznymi, do których należą definicje funkcji i deklaracje identyfikatorów. Te deklaracje i definicje mogą znajdować się w plikach źródłowych, plikach nagłówkowych, bibliotekach i innych plikach, które są potrzebne w programie. Należy skompilować każdą jednostkę translacji i połączyć pliki obiektów wynikowych w celu utworzenia programu.

„Program źródłowy” języka C jest kolekcją dyrektyw, pragm, deklaracji, definicji, bloków instrukcji i funkcji. Składniki programu Microsoft C muszą posiadać składnię opisaną w tym podręczniku, pomimo że mogą pojawiać się w dowolnej kolejności w programie (podlegają zasadom opisanym w tym podręczniku). Jednak lokalizacja tych składników w programie nie wpływa na to, jak zmienne i funkcje mogą być używane w programie. (Zobacz [okres istnienia, zakres, widoczność i połączenie,](../c-language/lifetime-scope-visibility-and-linkage.md) Aby uzyskać więcej informacji).

Pliki źródłowe nie muszą zawierać instrukcji wykonywalnych. Na przykład, może okazać się przydatne, aby umieszczać definicje zmiennych w jednym pliku źródłowym, a następnie deklarować odwołania do tych zmiennych w innych plikach źródłowych, które z nich korzystają. Ta technika sprawia, że definicje są łatwe do znalezienia i uaktualnienia w razie potrzeby. Z tego samego powodu stałe i makra są często organizowane w osobnych plikach nazywanych „plikami dołączanymi” lub „plikami nagłówkowymi”, do których można odwołać się w kodzie źródłowym, gdy jest to wymagane. Zobacz *Odwołanie preprocesora* , aby uzyskać informacje na temat [makr](../preprocessor/macros-c-cpp.md) i [plików dołączanych](../preprocessor/hash-include-directive-c-cpp.md).

## <a name="see-also"></a>Zobacz też

[Struktura programu](../c-language/program-structure.md)
