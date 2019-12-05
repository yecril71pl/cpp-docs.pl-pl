---
title: Podsumowanie deklaracji
ms.date: 11/04/2016
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
ms.openlocfilehash: 88cfc78089e0efd4765a40ab0d9c6dc333deb125
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857024"
---
# <a name="summary-of-declarations"></a>Podsumowanie deklaracji

*Deklaracja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;atrybut *-specyfikatory deklaracji* *-SEQ*<sub>opt</sub> *init-deklarator-list*<sub>opt</sub> **;**

*specyfikatory deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracji*<sub></sub> *specyfikatora klasy magazynu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracji*<sub></sub> *specyfikatora typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracji*<sub></sub> *kwalifikatora typu*

*Attribute-SEQ* :&nbsp;&nbsp;&nbsp;&nbsp;/\* \*specyficzne dla firmy Microsoft /<br/>
&nbsp;&nbsp;&nbsp;atrybut *atrybutu* &nbsp; *-SEQ*<sub>opt</sub>

*atrybut* : jeden z&nbsp;&nbsp;&nbsp;&nbsp;/\* \*firmy Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;[__asm](../assembler/inline/asm.md) [__clrcall](../cpp/clrcall.md) [__stdcall __based](../cpp/stdcall.md) [](../cpp/based-grammar.md) [__fastcall](../cpp/fastcall.md) [](../cpp/thiscall.md) [](../cpp/cdecl.md) __thiscall __cdecl [__inline](../cpp/inline-functions-cpp.md) [__vectorcall](../cpp/vectorcall.md)

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarator-list* **,** *init-deklarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator* **=** *inicjatora*  / \* inicjowania skalarne \*/

*storage-class-specifier*:<br/>
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
&nbsp;&nbsp;&nbsp;&nbsp;**volatile**

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarator *wskaźnika*"<sub>opt</sub> *Direct-"*

*deklarator Direct*:<br/>
&nbsp;&nbsp;&nbsp;*identyfikator* &nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(** *deklarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator* **[** *wyrażenie stałego wyrażenia*<sub>zgody</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator* **(** *Typ parametru-list* **)**  /\* New-Style deklarator \*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarator* **(** *opt z listą identyfikatorów*<sub></sub> **)**  /\* przestarzałego stylu deklarator \*

*wskaźnik*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *Typ kwalifikator*<sub></sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *Typ kwalifikatora listy*<sub></sub>

*parametr-type-list*:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/\* listy parametrów \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista parametrów*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista parametrów* **,...**

*Lista parametrów*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parametrów-list* **,** *deklaracji parametru*

*kwalifikator typu-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*kwalifikator typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*kwalifikator typu list* - *kwalifikator*

*Wyliczenie — specyfikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**rozliczanie** *identyfikatora*<sub></sub> wyliczenia **{** *Enumerator-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Wyliczenie**

*Lista modułów wyliczających*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*modułu wyliczającego*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*moduł wyliczający* **,** *moduł wyliczający*

*moduł wyliczający*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyliczenie — stała*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Wyliczenie — stałe* **=** *wyrażenie stałe*

*wyliczenie — stała*:<br/>
&nbsp;&nbsp;&nbsp;*identyfikator* &nbsp;

*struct-or-union-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;, w którym *identyfikatorem* *struktury lub Unii* jest<sub>wybór</sub> **{** *struct-deklaracji-list* **}**<br/>
&nbsp;&nbsp; *&nbsp;&nbsp;*

*struct-or-union*:<br/>
&nbsp;&nbsp; **&nbsp;&nbsp;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Unii**

*struct-declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struktury deklaracji*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura* *-Deklaracja* -list

*struct-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifier-qualifier-list* *struct-declarator-list* **;**

*specifier-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;*specyfikatora*<sub></sub> *typu* &nbsp;specyfikatora-kwalifikator<br/>
&nbsp;&nbsp;&nbsp;*specyfikator*<sub></sub> *kwalifikatora typu* &nbsp;

*struct-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-deklarator* *struct-deklarator-list* **,** *struct-deklarator*

*struct-declarator*:<br/>
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

*direct-abstract-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(** *abstract-deklarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-abstract-deklarator*<sub>opt</sub> **[** *wyrażenie stałe*<sub></sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bezpośrednie-abstrakcyjne-deklarator*<sub></sub> **(** *opt-Type-list*<sub></sub> **)**

*inicjator*:<br/>
*wyrażenie przypisania* &nbsp;&nbsp;&nbsp;&nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *inicjator-list* **}**  /\* do agregowania \*. /<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *inicjator — lista* **}**

*initializer-list*:<br/>
*inicjator* &nbsp;&nbsp;&nbsp;&nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inicjator listy* **,** *inicjator*

*Nazwa typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifier-qualifier-list* *abstract-declarator*<sub>opt</sub>

*typedef-Name*:<br/>
&nbsp;&nbsp;&nbsp;*identyfikator* &nbsp;

*Extended-decl-modyfikator-SEQ*:&nbsp;&nbsp;&nbsp;&nbsp;/\* \*firmy Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier-seq* *extended-decl-modifier*

*Extended-decl-modyfikator*:&nbsp;&nbsp;&nbsp;&nbsp;/\* specyficzne dla Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;**wątku** &nbsp;<br/>
&nbsp;&nbsp; **&nbsp;&nbsp;**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

## <a name="see-also"></a>Zobacz także

[Konwencje wywoływania](../cpp/calling-conventions.md)<br/>
[Gramatyka struktury fazy](../c-language/phrase-structure-grammar.md)<br/>
[Przestarzałe konwencje wywoływania](../cpp/obsolete-calling-conventions.md)