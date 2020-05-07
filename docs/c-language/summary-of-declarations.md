---
title: Podsumowanie deklaracji
ms.date: 11/04/2016
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
ms.openlocfilehash: e553f4bdfffcd4bba6a39b2d37af6ba25a3d65d9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170439"
---
# <a name="summary-of-declarations"></a>Podsumowanie deklaracji

*Deklaracja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja-specyfikators* *-SEQ*<sub>opt</sub> *init-deklarator-list*<sub>opt</sub> **;**

*specyfikatory deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja* *specyfikatora klasy magazynu* —<sub>wybór</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;Deklaracja *specyfikatora typu* *— wybór specyfikatorów*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;Deklaracja *kwalifikatora typu* *— wybór specyfikatorów*<sub>opt</sub>

*Attribute-SEQ* &nbsp; &nbsp; &nbsp; &nbsp; :/ specyficzny dla firmy Microsoft\*\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Attribute* *— atrybut-seq*<sub>opt</sub>

*atrybut* : jeden z&nbsp; &nbsp; &nbsp; &nbsp; / \* określonych przez firmę Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;[__asm](../assembler/inline/asm.md) [__clrcall](../cpp/clrcall.md) [__stdcall](../cpp/stdcall.md) [__based](../cpp/based-grammar.md) [__fastcall](../cpp/fastcall.md) [__thiscall](../cpp/thiscall.md) [__cdecl __inline](../cpp/cdecl.md) [__inline](../cpp/inline-functions-cpp.md) [__vectorcall](../cpp/vectorcall.md)

*init-deklarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarator-list*  **,**  *init-deklarator*

*init-deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator***=***initializer* inicjator / deklarator dla inicjalizacji\* skalarnej    \*/

*specyfikator klasy magazynu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Automatycznie**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**zarejestrować**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**ruchom**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**modyfikator**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**własne**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (** *rozszerzony-decl-modyfikator-SEQ* **)**  / \* specyficzny dla firmy Microsoft\*/

*specyfikator typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**pozycję**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**delikatn**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**wybierak**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**ZAOKR**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int8** / __int8\* specyficzny dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int16** / __int16\* specyficzny dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int32** / __int32\* specyficzny dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int64** / __int64\* specyficzny dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**długo**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**float**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Double**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**opatrzon**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**bajt**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-lub-Union-specyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum — specyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef — nazwa*

*kwalifikator typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**stała**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**volatile**

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>wybór</sub> wskaźnika *Direct-deklarator*

*deklarator Direct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identyfikatora*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(** *deklarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator* **[** *wybór wyrażenia stałego*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator* **(** *Typ parametru-list* **)**  / \* New-Style deklarator\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator* **(** nieważność *listy identyfikatorów*<sub>opt</sub> **)**  / \* — przestarzałe style deklarator\*/

*wskaźnik*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*Typ kwalifikatora —*<sub>wybór</sub> listy<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*Typ kwalifikatora —*<sub>opt</sub> *wskaźnik* wyboru listy

*Typ parametru-list*&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; :&nbsp; &nbsp; &nbsp; &nbsp; lista&nbsp; &nbsp; &nbsp; / \*\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista parametrów*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista parametrów* **,...**

*Lista parametrów*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja parametru*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista parametrów* **,** *Deklaracja parametru*

*kwalifikator typu-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*kwalifikator typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*kwalifikator typu —* *kwalifikator typu* list

*Wyliczenie — specyfikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**enum** *identifier*<sub>wybór</sub> identyfikatora wyliczenia **{** *Enumerator-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**enum** *Identyfikator* wyliczenia

*Lista modułów wyliczających*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*liczeni*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*moduł wyliczający — lista* **,** *moduł wyliczający*

*moduł wyliczający*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Wyliczenie — stała*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Wyliczenie —* **=** *wyrażenie* stałej stałej

*wyliczenie — stała*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identyfikatora*

*specyfikator struct-or-Union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<sub>wybór</sub> *identyfikatora* *struct-or-Union* **{** *struct-deklaracji-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator* *struktury lub Unii*

*struct-lub-Union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**konstrukcja**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Unii**

*Struktura-deklaracja-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura — deklaracja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Struktura *-Deklaracja list* — *Deklaracja*

*Deklaracja struktury*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specyfikator-kwalifikator list* - *deklarator-list* **;**

*specyfikator — lista kwalifikatorów*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Specyfikator *typu specyfikatora* - *kwalifikator —*<sub>wybór</sub> listy<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Specyfikator *kwalifikatora typu* —<sub>wybór</sub> *listy*

*struct-deklarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-deklarator* *struct-deklarator-list* **,** *struct-deklarator*

*Struktura-deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Typ-specyfikator* *deklarator*<sub>opt</sub> **:** *wyrażenie stałe*

*Deklaracja parametru*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specyfikatory deklaracji* *deklarator*  / \* o nazwie deklarator\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;abstrakcyjne *specyfikatory deklaracji* *-deklarator*<sub>opt</sub>  / \* anonimowe deklarator\*/

*Lista identyfikatorów*:/\* dla deklarator starego stylu\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identyfikatora*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator — lista* **,** *Identyfikator*

*abstrakcyjny-deklarator*:\* /używany z anonimową Deklaratory\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*przytrzymaj*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>wybór</sub> wskaźnika *bezpośredniego-abstract-deklarator*

*deklarator pośredni-abstrakcyjny*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(** *abstract-deklarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bezpośrednie-abstrakcyjne-deklarator*<sub>opt</sub> **[** *wybór wyrażenia stałego*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bezpośrednie-abstrakcyjne-deklarator*<sub>opt</sub> **(** opt *-Type-list*<sub>opt</sub> **)**

*inicjator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*przypisanie — wyrażenie*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *inicjator — lista* **}**  / \* dla inicjalizacji agregacji\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *inicjator — lista* **,}**

*Lista inicjalizatora*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*skład*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inicjator — lista* **,** *inicjator*

*Nazwa typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specyfikator-kwalifikator list* *abstract-deklarator*<sub>opt</sub>

*typedef-Name*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identyfikatora*

*Extended-decl-modyfikator-SEQ*:&nbsp; &nbsp; &nbsp; &nbsp; / \* specyficzny dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*rozszerzony-decl-modyfikator*<sub>wyboru</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl-modyfikator-SEQ* *Extended-decl-modyfikator*

*Extended-decl-modyfikator*:&nbsp; &nbsp; &nbsp; &nbsp; / \* specyficzny dla firmy Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nici**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**okiem**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

## <a name="see-also"></a>Zobacz też

[Konwencje wywoływania](../cpp/calling-conventions.md)<br/>
[Gramatyka struktury frazy](../c-language/phrase-structure-grammar.md)<br/>
[Przestarzałe konwencje wywoływania](../cpp/obsolete-calling-conventions.md)
