---
title: Podsumowanie deklaracji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9e5fe380d41b5d1e58a63b1aa0b99a239dee515
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="summary-of-declarations"></a>Podsumowanie deklaracji
`declaration`:  
 *Specyfikatory deklaracji atrybutu seq* <sub>opt</sub> *init deklarator listy*<sub>opt</sub>**;**  
  
 /\* *Atrybut seq* jest Specific Microsoft * /  
  
 *Specyfikatory deklaracji*:  
 *Specyfikatory deklaracji Specyfikator klasy magazynu*<sub>opcjonalnych</sub>  
  
 *Specyfikatory deklaracji specyfikatora typu*<sub>opcjonalnych</sub>  
  
 *Specyfikatory deklaracji kwalifikator typu*<sub>opcjonalnych</sub>  
  
 *Atrybut seq* : /\* *seq atrybutu* jest Specific firmy Microsoft \*/  
 *Atrybut seq atrybutu* <sub>opcjonalnych</sub>  
  
 *atrybut* : jeden z / * Specific firmy Microsoft \*/  
 ||||  
|-|-|-|  
|[__asm](../assembler/inline/asm.md)|[__clrcall](../cpp/clrcall.md)|[__stdcall](../cpp/stdcall.md)|  
|[__based](../cpp/based-grammar.md)|[__fastcall](../cpp/fastcall.md)|[__thiscall](../cpp/thiscall.md)|  
|[__cdecl](../cpp/cdecl.md)|[__inline](../cpp/inline-functions-cpp.md)|[__vectorcall](../cpp/vectorcall.md)|  
  
 *init-declarator-list*:  
 *init-declarator*  
  
 *init — deklarator — lista***,***init deklarator*  
  
 *init-declarator*:  
 *declarator*  
  
 *deklarator***=***inicjatora* / * dla inicjowania skalarne \*/  
  
 *storage-class-specifier*:  
 **auto**  
  
 **register**  
  
 **static**  
  
 **extern**  
  
 **Element TypeDef**  
  
 **__declspec (***rozszerzony decl — modyfikator seq***)** / * Specific firmy Microsoft \*/  
  
 *Specyfikator typu*:  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 `__int8` / * Określonych firmy Microsoft \*/  
  
 `__int16` / * Określonych firmy Microsoft \*/  
  
 `__int32` / * Określonych firmy Microsoft \*/  
  
 `__int64` / * Określonych firmy Microsoft \*/  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **Podpisany**  
  
 **Bez znaku**  
  
 *struct-or-union-specifier*  
  
 *enum-specifier*  
  
 *Nazwa typu TypeDef*  
  
 *Kwalifikator typu*:  
 **const**  
  
 `volatile`  
  
 `declarator`:  
 `pointer`<sub>OPT</sub> *bezpośrednio deklarator*  
  
 *deklarator bezpośrednio*:  
 *Identyfikator*  
  
 **(***deklarator***)**  
  
 *deklarator bezpośrednio***[***wyrażenia* <sub>opt</sub>**]**  
  
 *deklarator bezpośrednio***(***listy parametrów typu***)** / * nowy styl deklarator \*/  
  
 *deklarator bezpośrednio***(***listy identyfikatorów*<sub>opt</sub>**)** / * przestarzały styl deklarator \*/  
  
 `pointer`:  
 **\*** *Lista typów kwalifikator*<sub>opcjonalnych</sub>  
  
 **\*** *Lista typów kwalifikator*<sub>opcjonalnych</sub>`pointer`  
  
 *listy parametrów typu*: /\* listy parametrów \*/  
 *parameter-list*  
  
 *parameter-list* **, ...**  
  
 *Lista parametrów*:  
 *Deklaracja parametru*  
  
 *Lista parametrów***,***deklaracji parametru*  
  
 *Lista typów kwalifikator*:  
 *type-qualifier*  
  
 *Kwalifikator typu listy kwalifikator — typ*  
  
 *Specyfikator wyliczenia*:  
 **wyliczenia***identyfikator*<sub>opt</sub>**{** *listy modułu wyliczającego* **}**  
  
 **wyliczenia***identyfikator*  
  
 *Moduł wyliczający listy*:  
 *enumerator*  
  
 *Moduł wyliczający listy***,**  `enumerator`  
  
 `enumerator`:  
 *Stała wyliczenia*  
  
 *Stała wyliczenia***=***wyrażenie stałej*  
  
 *Stała wyliczenia*:  
 *Identyfikator*  
  
 *struct-or-union-specifier*:  
 *Identyfikator struktury lub Unii*<sub>opt</sub>**{** *struktury deklaracji listy* **}** *struktury lub związku Identyfikator*  
  
 *struct-or-union*:  
 **struct**  
  
 **Unii**  
  
 *struct-declaration-list*:  
 *struct-declaration*  
  
 *Deklaracja struktury deklaracjach — struktura*  
  
 *struct-declaration*:  
 *Specyfikator kwalifikator listy w strukturze listy deklarator***;**  
  
 *specifier-qualifier-list*:  
 *Specyfikator typu w specyfikatorze listy kwalifikator*<sub>opcjonalnych</sub>  
  
 *Kwalifikator typu w specyfikatorze listy kwalifikator*<sub>opcjonalnych</sub>  
  
 *struct-declarator-list*:  
 *deklarator struktury w strukturze listy deklarator***,***deklarator — struktura*  
  
 *struct-declarator*:  
 *declarator*  
  
 *Specyfikator typu deklarator*<sub>opt</sub>**:** *wyrażenie stałej*  
  
 *Deklaracja parametru*:  
 *Specyfikatory deklaracji deklarator* / * nazwa deklarator \*/  
  
 *Specyfikatory deklaracji abstrakcyjny — deklarator*<sub>opt</sub> **/ \*** deklarator anonimowe **\*/**  
  
 *Lista identyfikatorów*: **/ \*** dla deklaratora w starym stylu **\* /**  
 *Identyfikator*  
  
 *Lista identyfikatorów***,***identyfikator*  
  
 *deklarator abstrakcyjny*: **/ \*** używane z anonimowego deklaratorów **\*/**  
 *pointer*  
  
 `pointer`<sub>opt</sub>*direct-abstract-declarator*  
  
 *direct-abstract-declarator*:  
 **(***deklarator abstrakcyjny***)**  
  
 *direct-abstract-declarator*<sub>opt</sub>**[** *constant-expression*<sub>opt</sub>**]**  
  
 *bezpośrednie abstrakcyjny — deklarator*<sub>opt</sub>**(** *listy parametrów typu* <sub>opt</sub>**)**  
  
 *Inicjator*:  
 *assignment-expression*  
  
 **{***listy inicjatorów***}** / * dla inicjowania agregacji \*/  
  
 **{***listy inicjatorów***,}**   
  
 *initializer-list*:  
 *initializer*  
  
 *Lista inicjalizatora***,***inicjatora*  
  
 *Nazwa typu*:  
 *Specyfikator kwalifikator listy abstrakcyjny — deklarator*<sub>opcjonalnych</sub>  
  
 *Nazwa typu TypeDef*:  
 *Identyfikator*  
  
 *rozszerzony decl — modyfikator seq*:/\* Specific firmy Microsoft \*/  
 *rozszerzony decl — modyfikator*<sub>opcjonalnych</sub>  
  
 *rozszerzony rozszerzony decl — modyfikator seq — decl — modyfikator*  
  
 *rozszerzony decl — modyfikator*: /\* Specific firmy Microsoft \*/  
 **wątek**  
  
 **naked**  
  
 **DllImport**  
  
 `dllexport`  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencje wywoływania](../cpp/calling-conventions.md)   
 [Gramatyka struktury fazy](../c-language/phrase-structure-grammar.md)   
 [Przestarzałe konwencje wywoływania](../cpp/obsolete-calling-conventions.md)