---
title: Podsumowanie deklaracji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 61dae4cf26f881014f0d98bbf30ebd10a360b10f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="summary-of-declarations"></a>Podsumowanie deklaracji
`declaration`:  
 *Specyfikatory deklaracji atrybutu seq* <sub>opt</sub> *init deklarator listy*<sub>opt</sub>**;**  
  
 /\**seq atrybutu* jest Specific Microsoft * /  
  
 *Specyfikatory deklaracji*:  
 *Specyfikatory deklaracji Specyfikator klasy magazynu*<sub>opcjonalnych</sub>  
  
 *Specyfikatory deklaracji specyfikatora typu*<sub>opcjonalnych</sub>  
  
 *Specyfikatory deklaracji kwalifikator typu*<sub>opcjonalnych</sub>  
  
 *Atrybut seq* : /\* *seq atrybutu* jest Specific firmy Microsoft\*/  
 *Atrybut seq atrybutu* <sub>opcjonalnych</sub>  
  
 *atrybut* : jeden z / * Specific firmy Microsoft\*/  
 ||||  
|-|-|-|  
|[__asm](../assembler/inline/asm.md)|[__clrcall](../cpp/clrcall.md)|[__stdcall](../cpp/stdcall.md)|  
|[__based](../cpp/based-grammar.md)|[__fastcall](../cpp/fastcall.md)|[__thiscall](../cpp/thiscall.md)|  
|[__cdecl](../cpp/cdecl.md)|[__inline](../cpp/inline-functions-cpp.md)|[__vectorcall](../cpp/vectorcall.md)|  
  
 *init — deklarator — lista*:  
 *init — deklarator*  
  
 *init — deklarator — lista***,***init deklarator*   
  
 *init — deklarator*:  
 *deklarator*  
  
 *deklarator***=***inicjatora* / * dla inicjowania skalarne    \*/  
  
 *Specyfikator klasy magazynu*:  
 **Automatycznie**  
  
 **Rejestr**  
  
 **static**  
  
 **extern**  
  
 **Element TypeDef**  
  
 **__declspec (***rozszerzony decl — modyfikator seq***)** / * Specific firmy Microsoft    \*/  
  
 *Specyfikator typu*:  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 `__int8`/ * Określonych firmy Microsoft\*/  
  
 `__int16`/ * Określonych firmy Microsoft\*/  
  
 `__int32`/ * Określonych firmy Microsoft\*/  
  
 `__int64`/ * Określonych firmy Microsoft\*/  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **podpisany**  
  
 **bez znaku**  
  
 *Specyfikator Struct lub union*  
  
 *Enum — Specyfikator*  
  
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
  
 *deklarator bezpośrednio***(***listy parametrów typu***)** / * nowy styl deklarator      \*/  
  
 *deklarator bezpośrednio***(***listy identyfikatorów*<sub>opt</sub>**)** / * przestarzały styl deklarator    \*/  
  
 `pointer`:  
 **\****typu kwalifikator listy*<sub>opcjonalnych</sub>  
  
 **\****typu kwalifikator listy*<sub>opcjonalnych</sub>`pointer`  
  
 *listy parametrów typu*: /\* listy parametrów\*/  
 *listy parametrów*  
  
 *Lista parametrów* **,...**  
  
 *Lista parametrów*:  
 *Deklaracja parametru*  
  
 *Lista parametrów***,***deklaracji parametru*   
  
 *Lista typów kwalifikator*:  
 *Kwalifikator typu*  
  
 *Kwalifikator typu listy kwalifikator — typ*  
  
 *Specyfikator wyliczenia*:  
 **wyliczenia***identyfikator*<sub>opt</sub>**{** *listy modułu wyliczającego* **}**   
  
 **wyliczenia***identyfikator*   
  
 *Moduł wyliczający listy*:  
 *Moduł wyliczający*  
  
 *Moduł wyliczający listy***,**   `enumerator`  
  
 `enumerator`:  
 *Stała wyliczenia*  
  
 *Stała wyliczenia***=***wyrażenie stałej*   
  
 *Stała wyliczenia*:  
 *Identyfikator*  
  
 *Specyfikator Struct lub union*:  
 *Identyfikator struktury lub Unii*<sub>opt</sub>**{** *struktury deklaracji listy* **}**  *Identyfikator struktury lub związku*  
  
 *Struktura lub Unia*:  
 **struct**  
  
 **Unii**  
  
 *Struktura deklaracji listy*:  
 *Deklaracja — struktura*  
  
 *Deklaracja struktury deklaracjach — struktura*  
  
 *Deklaracja struktury*:  
 *Specyfikator kwalifikator listy w strukturze listy deklarator***;**   
  
 *Specyfikator kwalifikator listy*:  
 *Specyfikator typu w specyfikatorze listy kwalifikator*<sub>opcjonalnych</sub>  
  
 *Kwalifikator typu w specyfikatorze listy kwalifikator*<sub>opcjonalnych</sub>  
  
 *Struktura deklarator listy*:  
 *deklarator struktury w strukturze listy deklarator***,***deklarator — struktura*   
  
 *Struktura deklarator*:  
 *deklarator*  
  
 *Specyfikator typu deklarator*<sub>opt</sub>**:** *wyrażenie stałej*  
  
 *Deklaracja parametru*:  
 *Specyfikatory deklaracji deklarator* / * nazwa deklarator\*/  
  
 *Specyfikatory deklaracji abstrakcyjny — deklarator*<sub>opt</sub>  **/ \***  deklarator anonimowe**\*/**  
  
 *Lista identyfikatorów*:  **/ \***  dla deklaratora w starym stylu**\* /**  
 *Identyfikator*  
  
 *Lista identyfikatorów***,***identyfikator*   
  
 *deklarator abstrakcyjny*:  **/ \***  używane z anonimowego deklaratorów**\*/**  
 *wskaźnik*  
  
 `pointer`<sub>OPT</sub>*bezpośrednio abstrakcyjny — deklarator*  
  
 *bezpośrednie abstrakcyjny — deklarator*:  
 **(***deklarator abstrakcyjny***)**   
  
 *bezpośrednie abstrakcyjny — deklarator*<sub>opt</sub>**[** *wyrażenia*<sub>opt</sub>**]**  
  
 *bezpośrednie abstrakcyjny — deklarator*<sub>opt</sub>**(** *listy parametrów typu* <sub>opt</sub>**)**  
  
 *Inicjator*:  
 *wyrażenia przypisania*  
  
 **{***listy inicjatorów***}** / * dla inicjowania agregacji    \*/  
  
 **{***listy inicjatorów***,}**   
  
 *listy inicjatorów*:  
 *Inicjator*  
  
 *Lista inicjalizatora***,***inicjatora*   
  
 *Nazwa typu*:  
 *Specyfikator kwalifikator listy abstrakcyjny — deklarator*<sub>opcjonalnych</sub>  
  
 *Nazwa typu TypeDef*:  
 *Identyfikator*  
  
 *rozszerzony decl — modyfikator seq*:/\* Specific firmy Microsoft\*/  
 *rozszerzony decl — modyfikator*<sub>opcjonalnych</sub>  
  
 *rozszerzony rozszerzony decl — modyfikator seq — decl — modyfikator*  
  
 *rozszerzony decl — modyfikator*: /\* Specific firmy Microsoft\*/  
 **wątek**  
  
 **naked**  
  
 **DllImport**  
  
 `dllexport`  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencje wywoływania](../cpp/calling-conventions.md)   
 [Gramatyka struktury fazy](../c-language/phrase-structure-grammar.md)   
 [Przestarzałe konwencje wywoływania](../cpp/obsolete-calling-conventions.md)