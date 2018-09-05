---
title: Pliki źródłowe i programy źródłowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- files [C++], source
- programs [C++], source
- source files, specifying in compiler
- source programs
ms.assetid: 18bb2826-17da-48e5-92a2-10e649f1bc9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5189f1e9467977afda919862005901a633dae6a7
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765164"
---
# <a name="source-files-and-source-programs"></a>Pliki źródłowe i programy źródłowe
Program źródłowy można podzielić na jeden lub więcej „plików źródłowych” lub „jednostek translacji”. Dane wejściowe kompilatora nazywane są „jednostką translacji”.  
  
## <a name="syntax"></a>Składnia

*jednostki translacji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja zewnętrzne* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*jednostki translacji* *deklaracji zewnętrzne*  
  
*Deklaracja zewnętrzne*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Definicja funkcji*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja*

[Przegląd deklaracji](../c-language/overview-of-declarations.md) podaje składnię dla `declaration` nieterminalnych i *Preprocessor Reference* wyjaśnia sposób, w jaki [jednostki translacji](../preprocessor/phases-of-translation.md) jest przetwarzany.  
  
> [!NOTE]
>  Zobacz wprowadzenie do [podsumowanie dotyczące składni języka C](../c-language/c-language-syntax-summary.md), objaśnienia dotyczące Konwencji składni ANSI.  
  
Składniki jednostki translacji są deklaracjami zewnętrznymi, do których należą definicje funkcji i deklaracje identyfikatorów. Te deklaracje i definicje mogą znajdować się w plikach źródłowych, plikach nagłówkowych, bibliotekach i innych plikach, które są potrzebne w programie. Należy skompilować każdą jednostkę translacji i połączyć pliki obiektów wynikowych w celu utworzenia programu.  
  
„Program źródłowy” języka C jest kolekcją dyrektyw, pragm, deklaracji, definicji, bloków instrukcji i funkcji. Składniki programu Microsoft C muszą posiadać składnię opisaną w tym podręczniku, pomimo że mogą pojawiać się w dowolnej kolejności w programie (podlegają zasadom opisanym w tym podręczniku). Jednak lokalizacja tych składników w programie nie wpływa na to, jak zmienne i funkcje mogą być używane w programie. (Zobacz [okres istnienia, zakres, widoczność i powiązania](../c-language/lifetime-scope-visibility-and-linkage.md) Aby uzyskać więcej informacji.)  
  
Pliki źródłowe nie muszą zawierać instrukcji wykonywalnych. Na przykład, może okazać się przydatne, aby umieszczać definicje zmiennych w jednym pliku źródłowym, a następnie deklarować odwołania do tych zmiennych w innych plikach źródłowych, które z nich korzystają. Ta technika sprawia, że definicje są łatwe do znalezienia i uaktualnienia w razie potrzeby. Z tego samego powodu stałe i makra są często organizowane w osobnych plikach nazywanych „plikami dołączanymi” lub „plikami nagłówkowymi”, do których można odwołać się w kodzie źródłowym, gdy jest to wymagane. Zobacz *Preprocessor Reference* uzyskać informacji na temat [makra](../preprocessor/macros-c-cpp.md) i [pliki dołączane](../preprocessor/hash-include-directive-c-cpp.md).  
  
## <a name="see-also"></a>Zobacz też  
[Struktura programu](../c-language/program-structure.md)