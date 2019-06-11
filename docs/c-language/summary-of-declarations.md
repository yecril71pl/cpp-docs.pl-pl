---
title: Podsumowanie deklaracji
ms.date: 11/04/2016
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
ms.openlocfilehash: 21d6866f8e0b370d8a0d93253a6259302666963a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157743"
---
# <a name="summary-of-declarations"></a>Podsumowanie deklaracji

*Deklaracja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *attribute-seq*<sub>opt</sub> *init-declarator-list*<sub>opt</sub> **;**

*Specyfikatory deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Storage-class-specifier* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kwalifikator typu* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub>

*Atrybut seq* :&nbsp;&nbsp;&nbsp;&nbsp;/\* Specyficzne dla firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*attribute* *attribute-seq*<sub>opt</sub>

*atrybut* : jeden z&nbsp; &nbsp; &nbsp; &nbsp; / \* Specific firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;[__asm](../assembler/inline/asm.md) [__clrcall](../cpp/clrcall.md) [__stdcall](../cpp/stdcall.md) [__based](../cpp/based-grammar.md) [__fastcall](../cpp/fastcall.md) [__thiscall](../cpp/thiscall.md) [__cdecl](../cpp/cdecl.md) [__inline](../cpp/inline-functions-cpp.md) [__vectorcall](../cpp/vectorcall.md)

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-list*  **,**  *init-declarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator* **=** *inicjatora*  / \* inicjowania skalarne \*/

*storage-class-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**auto**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**register**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Statyczne**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Element TypeDef**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__declspec (** *extended-decl modyfikator seq* **)**  / \* Specific firmy Microsoft \*/

*Specyfikator typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Void**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**short**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int8**  / \* specyficzne dla firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int16**  / \* specyficzne dla firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int32**  / \* specyficzne dla firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int64**  / \* specyficzne dla firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**długi**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**float**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**double**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Podpisany**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Bez znaku**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu wyliczeniowego*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-name*

*Kwalifikator typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**const**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**volatile**

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wskaźnik*<sub>zoptymalizowany pod kątem</sub> *deklaratora bezpośrednie*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(** *deklaratora* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio* **[** *wyrażenie_stałe*<sub>zoptymalizowany pod kątem</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio* **(** *listy parametrów typu* **)**  / \* deklaratora nowy styl \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio* **(** *listy identyfikatorów*<sub>zoptymalizowany pod kątem</sub> **)**  / \* Obsolete stylu deklarator \*/

*pointer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *Lista typów kwalifikator*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *Lista typów kwalifikator*<sub>zoptymalizowany pod kątem</sub> *wskaźnika*

*listy parametrów typu*:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/\* Lista parametrów \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **, ...**

*parameter-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **,** *parameter-declaration*

*Lista typów kwalifikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kwalifikator typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista typów kwalifikator* *kwalifikator typu*

*Specyfikator typu wyliczeniowego*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**wyliczenie** *identyfikator*<sub>zoptymalizowany pod kątem</sub> **{** *lista_modułów_wyliczających* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**wyliczenie** *identyfikator*

*enumerator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Moduł wyliczający*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Moduł wyliczający listę* **,** *modułu wyliczającego*

*Moduł wyliczający*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Stała wyliczenia*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Stała wyliczenia* **=** *wyrażenia stałego*

*Stała wyliczenia*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

*struct-or-union-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struktury lub Unii* *identyfikator*<sub>zoptymalizowany pod kątem</sub> **{** *struktury deklaracji listy* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struktury lub Unii* *identyfikator*

*struct-or-union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**struct**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Unia**

*struct-declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura deklaracji listy* *deklaracji struktury*

*struct-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifier-qualifier-list* *struct-declarator-list* **;**

*specifier-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu* *specyfikator kwalifikator listy*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kwalifikator typu* *specyfikator kwalifikator listy*<sub>zoptymalizowany pod kątem</sub>

*struct-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declarator* *struct-declarator-list* **,** *struct-declarator*

*struct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu* *deklaratora*<sub>zoptymalizowany pod kątem</sub> **:** *wyrażenia stałego*

*parameter-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji* *deklaratora*  / \* deklaratora nazwane \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji* *abstrakcyjny declarator*<sub>zoptymalizowany pod kątem</sub>  / \* deklaratora anonimowe \*/

*Lista identyfikatorów*: /\* dla deklaratora w starym stylu \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista identyfikatorów* **,** *identyfikator*

*deklarator abstrakcyjny*: /\* używane z deklaratorów anonimowe \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Wskaźnik*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-abstract-declarator*

*direct-abstract-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(** *abstract-declarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*bezpośrednie abstrakcyjny declarator*<sub>zoptymalizowany pod kątem</sub> **[** *wyrażenie_stałe*<sub>zoptymalizowany pod kątem</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-abstract-declarator*<sub>opt</sub> **(** *parameter-type-list*<sub>opt</sub> **)**

*initializer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *listy inicjatorów* **}**  / \* dla inicjowania agregacji \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *initializer-list* **, }**

*initializer-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Inicjator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*listy inicjatorów* **,** *inicjatora*

*Nazwa typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifier-qualifier-list* *abstract-declarator*<sub>opt</sub>

*Nazwa TypeDef*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

*extended-decl-modifier-seq*:&nbsp;&nbsp;&nbsp;&nbsp;/\* Specyficzne dla firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier-seq* *extended-decl-modifier*

*extended-decl-modifier*:&nbsp;&nbsp;&nbsp;&nbsp;/\* Specyficzne dla firmy Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Wątek**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

## <a name="see-also"></a>Zobacz także

[Konwencje wywoływania](../cpp/calling-conventions.md)<br/>
[Gramatyka struktury fazy](../c-language/phrase-structure-grammar.md)<br/>
[Przestarzałe konwencje wywoływania](../cpp/obsolete-calling-conventions.md)