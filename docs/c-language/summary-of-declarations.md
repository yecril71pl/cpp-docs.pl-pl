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
&nbsp;&nbsp;&nbsp;&nbsp;atrybut *-specyfikatory deklaracji* *-SEQ*<sub>opt</sub> *init-deklarator-list*<sub>opt</sub> **;**

*specyfikatory deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracji*<sub>opt</sub> *specyfikatora klasy magazynu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracji*<sub>opt</sub> *specyfikatora typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracji*<sub>opt</sub> *kwalifikatora typu*

*Attribute-SEQ* :&nbsp;&nbsp;&nbsp;&nbsp;/\* \*specyficzne dla firmy Microsoft /<br/>
&nbsp;&nbsp;&nbsp;atrybut *atrybutu* &nbsp; *-SEQ*<sub>opt</sub>

*atrybut* : jeden z&nbsp;&nbsp;&nbsp;&nbsp;/\* \*firmy Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;[__asm](../assembler/inline/asm.md) [__clrcall](../cpp/clrcall.md) [__stdcall __based](../cpp/stdcall.md) [__based](../cpp/based-grammar.md) [__fastcall](../cpp/fastcall.md) [__thiscall](../cpp/thiscall.md) [__cdecl](../cpp/cdecl.md) __thiscall __cdecl [__inline](../cpp/inline-functions-cpp.md) [__vectorcall](../cpp/vectorcall.md)

*init-deklarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarator-list* **,** *init-deklarator*

*init-deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator* **=** *inicjator* /\* do inicjowania skalarnego \*/

*specyfikator klasy magazynu*:<br/>
&nbsp;&nbsp; **&nbsp;&nbsp;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**register**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**static**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**typedef**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__declspec (** *rozszerzony-decl-modyfikator-SEQ* **)**  /\* \*/

*specyfikator typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**void**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Short**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int8** /\* \*firmy Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int16** /\* \*firmy Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int32** /\* \*firmy Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int64** /\* \*firmy Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**długa**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**zmiennoprzecinkowe**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Double**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**podpisane**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**bez znaku**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-lub-Union-specyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Wyliczenie*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-Name*

*kwalifikator typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**const**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nietrwałe**

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarator *wskaźnika*"<sub>opt</sub> *Direct-"*

*deklarator Direct*:<br/>
&nbsp;&nbsp;&nbsp;*identyfikator* &nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(** *deklarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator* **[** *wyrażenie stałego wyrażenia*<sub>zgody</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator* **(** *Typ parametru-list* **)**  /\* New-Style deklarator \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator* **(** *opt z listą identyfikatorów*<sub>opt</sub> **)**  /\* przestarzałego stylu deklarator \*/

*wskaźnik*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *Typ kwalifikator*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *Typ kwalifikatora listy*<sub>opt</sub> *pointer*

*parametr-type-list*:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/\* listy parametrów \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista parametrów*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista parametrów* **,...**

*Lista parametrów*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracji parametru*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parametrów-list* **,** *deklaracji parametru*

*kwalifikator typu-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*kwalifikator typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*kwalifikator typu list* - *kwalifikator*

*Wyliczenie — specyfikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**rozliczanie** *identyfikatora*<sub>opt</sub> wyliczenia **{** *Enumerator-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Wyliczenie** *identifier*

*Lista modułów wyliczających*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*modułu wyliczającego*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*moduł wyliczający* **,** *moduł wyliczający*

*moduł wyliczający*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyliczenie — stała*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Wyliczenie — stałe* **=** *wyrażenie stałe*

*wyliczenie — stała*:<br/>
&nbsp;&nbsp;&nbsp;*identyfikator* &nbsp;

*specyfikator struct-or-Union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;, w którym *identyfikatorem* *struktury lub Unii* jest<sub>wybór</sub> **{** *struct-deklaracji-list* **}**<br/>
&nbsp;&nbsp; *&nbsp;&nbsp;* *identifier*

*struct-lub-Union*:<br/>
&nbsp;&nbsp; **&nbsp;&nbsp;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Unii**

*Struktura-deklaracja-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struktury deklaracji*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura* *-Deklaracja* -list

*Deklaracja struktury*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specyfikator-list kwalifikator* - *deklarator-list* **;**

*specyfikator — lista kwalifikatorów*:<br/>
&nbsp;&nbsp;&nbsp;*specyfikatora*<sub>opt</sub> *typu* &nbsp;specyfikatora-kwalifikator<br/>
&nbsp;&nbsp;&nbsp;*specyfikator*<sub>opt</sub> *kwalifikatora typu* &nbsp;

*struct-deklarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-deklarator* *struct-deklarator-list* **,** *struct-deklarator*

*Struktura-deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specyfikator typu* *deklarator*<sub>opt</sub> **:** *wyrażenie stałe*

*Deklaracja parametru*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracji-specyfikatory* *deklarator* /\* o nazwie deklarator \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specyfikatorów deklaracji-* *deklarator*<sub>opt</sub> /\* anonimowe deklarator \*/

*Lista identyfikatorów*:/\* dla starego stylu \*deklarator /<br/>
&nbsp;&nbsp;&nbsp;*identyfikator* &nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator listy* **,** *Identyfikator*

*abstrakcyjny-deklarator*:/\* używany z anonimowymi \*Deklaratory /<br/>
&nbsp;&nbsp; *&nbsp;&nbsp;*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wskaźnik*<sub>opt</sub> - *abstract-deklarator*

*deklarator pośredni-abstrakcyjny*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(** *abstract-deklarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-abstract-deklarator*<sub>opt</sub> **[** *wyrażenie stałe*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bezpośrednie-abstrakcyjne-deklarator*<sub>opt</sub> **(** *opt-Type-list*<sub>opt</sub> **)**

*inicjator*:<br/>
*wyrażenie przypisania* &nbsp;&nbsp;&nbsp;&nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *inicjator-list* **}**  /\* do agregowania \*. /<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *inicjator — lista* **}**

*Lista inicjalizatora*:<br/>
*inicjator* &nbsp;&nbsp;&nbsp;&nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inicjator listy* **,** *inicjator*

*Nazwa typu*:<br/>
&nbsp;&nbsp;&nbsp;*specyfikator &nbsp;kwalifikator-list* - *deklarator*<sub>opt</sub>

*typedef-Name*:<br/>
&nbsp;&nbsp;&nbsp;*identyfikator* &nbsp;

*Extended-decl-modyfikator-SEQ*:&nbsp;&nbsp;&nbsp;&nbsp;/\* \*firmy Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*rozszerzony-decl-modyfikator*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*rozszerzony-decl-modyfikator-SEQ* *Extended-decl-modyfikator*

*Extended-decl-modyfikator*:&nbsp;&nbsp;&nbsp;&nbsp;/\* specyficzne dla Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;**wątku** &nbsp;<br/>
&nbsp;&nbsp; **&nbsp;&nbsp;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

## <a name="see-also"></a>Zobacz też

[Konwencje wywoływania](../cpp/calling-conventions.md)<br/>
[Gramatyka struktury fazy](../c-language/phrase-structure-grammar.md)<br/>
[Przestarzałe konwencje wywoływania](../cpp/obsolete-calling-conventions.md)
